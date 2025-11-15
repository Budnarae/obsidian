---
tags:
  - game
  - Unreal_Engine
---

_Animation 간 전환_

---

# 📘 **FAnimStateTransition — Cheat Sheet**

---

# 🟦 1. 헤더 파일 의사 코드

```cpp
// ============================================================================
// FAnimStateTransition (의사 코드)
// AnimStateMachine 내 State 간 Transition 정보 관리
// Condition, BlendTime, Source/Target State를 포함
// ============================================================================
struct FAnimStateTransition
{
public:

    // ------------------------------------------------------------------------
    // Transition 이름
    // 디버깅용, 유니크 식별자
    // ------------------------------------------------------------------------
    FName TransitionName;

    // ------------------------------------------------------------------------
    // Source / Target State
    // Transition 출발 상태와 도착 상태 포인터
    // ------------------------------------------------------------------------
    struct FAnimState* SourceState;
    struct FAnimState* TargetState;

    // ------------------------------------------------------------------------
    // Transition 조건
    // true가 되면 Transition 발동
    // ------------------------------------------------------------------------
    std::function<bool()> CanEnterTransition;

    // ------------------------------------------------------------------------
    // Transition 블렌딩 시간
    // ActiveState Pose -> TargetState Pose로 자연스럽게 Blend
    // ------------------------------------------------------------------------
    float BlendTime = 0.2f;

    // ------------------------------------------------------------------------
    // Interrupt 옵션
    // 다른 Transition으로 중단 가능한지 여부
    // ------------------------------------------------------------------------
    bool bCanInterrupt = true;

    // ------------------------------------------------------------------------
    // Transition 진행 상태
    // BlendAlpha: 0.0 = SourcePose, 1.0 = TargetPose
    // ------------------------------------------------------------------------
    float BlendAlpha = 0.0f;

public:

    // ------------------------------------------------------------------------
    // Update
    // DeltaTime 기반으로 BlendAlpha 계산
    // Condition 평가 후 Blend 진행
    // ------------------------------------------------------------------------
    void Update(float DeltaTime)
    {
        if (CanEnterTransition && CanEnterTransition())
        {
            BlendAlpha += DeltaTime / BlendTime;
            if (BlendAlpha > 1.f)
                BlendAlpha = 1.f;
        }
        else
        {
            BlendAlpha = 0.f;
        }
    }

    // ------------------------------------------------------------------------
    // Evaluate
    // SourcePose와 TargetPose를 BlendAlpha 기준으로 보간
    // ------------------------------------------------------------------------
    FPose Evaluate(const FPose& SourcePose, const FPose& TargetPose)
    {
        return FPose::Blend(SourcePose, TargetPose, BlendAlpha);
    }
};
```

---

# 🟦 2. 핵심 역할 요약

|기능|설명|
|---|---|
|**Source/Target State 관리**|어느 상태에서 어느 상태로 전환될지 저장|
|**Transition 조건 평가**|CanEnterTransition 함수로 true/false 판단|
|**Blend 계산**|BlendTime 동안 Pose를 보간하여 자연스러운 전환|
|**Interrupt 처리**|다른 Transition으로 중단 가능한지 여부 관리|
|**Transition 진행 상태 저장**|BlendAlpha 0~1, 현재 Transition 진행률|

---

# 🟦 3. 기능별 상세 설명

### 🔹 Condition 평가

```cpp
bool bTrigger = CanEnterTransition();
```

- true → Transition 발동 시작
    
- false → 현재 상태 유지
    

### 🔹 Blend 계산

```cpp
BlendAlpha += DeltaTime / BlendTime;
BlendAlpha = FMath::Clamp(BlendAlpha, 0.f, 1.f);
```

- 0 → SourcePose
    
- 1 → TargetPose
    
- Evaluate 시 BlendAlpha 기준으로 Pose 보간
    

### 🔹 Evaluate

```cpp
FPose ResultPose = FPose::Blend(SourcePose, TargetPose, BlendAlpha);
```

- Transition 활성 시 Source와 Target Pose를 보간
    
- AnimGraph Evaluate 단계에서 호출됨
    

---

# 🟦 4. ASM Update/Evaluate에서의 위치

```
FAnimNode_StateMachine.Update():
    └─ CurrentActiveState.Transitions:
            └─ FAnimStateTransition.Update(DeltaTime)
                └─ Condition 체크
                └─ BlendAlpha 계산

FAnimNode_StateMachine.Evaluate():
    └─ ActiveState Pose
    └─ BlendAlpha>0 → Evaluate(SourcePose, TargetPose)
    └─ 최종 Pose 출력
```

---

# 🟦 5. 요약

- **FAnimStateTransition** = StateMachine 내 상태 전환 단위
    
- Condition 평가, BlendTime 처리, ActiveState → TargetState Pose 보간을 담당
    
- Transition 자체는 구조체로 존재하며, 실제 Pose 블렌딩은 Evaluate에서 처리
    
- ASM에서 Transition CRUD 및 Update/Evaluate의 핵심 처리 단위
    