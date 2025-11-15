---
tags:
  - game
  - Unreal_Engine
---

_하나의 애니메이션을 재생하는 기본 노드_

---

# 📘 **FAnimNode_SequencePlayer — Cheat Sheet**

---

# 🟦 1. 헤더 파일 의사 코드 (멤버 변수 + 멤버 함수 선언)

```cpp
// =====================================================================================
// FAnimNode_SequencePlayer (의사 코드 버전)
// 단일 애니메이션(AnimSequence / AnimSequenceBase)을 시간에 따라 재생하는 노드
// Update = 재생 시간 증가, Evaluate = 해당 시간의 Pose 계산
// =====================================================================================

struct FAnimNode_SequencePlayer : public FAnimNode_Base
{
public:

    // ----------------------------------------------------------------------
    // 1) Update Phase (재생 시간 진행, 루프/속도 처리)
    // ----------------------------------------------------------------------

    // void Update_AnyThread(const FAnimationUpdateContext& Context)
    // - DeltaTime 기반으로 재생 시간 업데이트
    // - PlayRate 적용 및 Loop 처리
    virtual void Update_AnyThread(const FAnimationUpdateContext& Context) override;

    // float AdvanceTime(float DeltaTime)
    // - 현재 PlayRate에 따라 TimeCursor 증가 후 반환
    float AdvanceTime(float DeltaTime);


    // ----------------------------------------------------------------------
    // 2) Evaluate Phase (해당 시점의 Pose 계산)
    // ----------------------------------------------------------------------

    // void Evaluate_AnyThread(FPoseContext& Output)
    // - Sequence에서 현재 시간의 Pose를 Sampling하여 Output에 기록
    virtual void Evaluate_AnyThread(FPoseContext& Output) override;


    // ----------------------------------------------------------------------
    // 3) Playback Control
    // ----------------------------------------------------------------------

    // void SetPlayRate(float NewRate)
    // - 재생 속도 설정
    void SetPlayRate(float NewRate);

    // void SetPosition(float NewPosition)
    // - 현재 재생 시간을 강제로 변경
    void SetPosition(float NewPosition);

    // float GetCurrentTime() const
    // - 현재 재생 시간 반환
    float GetCurrentTime() const;


protected:

    // ========================
    // Internal Data
    // ========================

    // 재생할 애니메이션
    UAnimSequenceBase* Sequence;

    // 현재 재생 시간
    float CurrentTime;

    // 재생 속도 (1.0 = 정상)
    float PlayRate;

    // 루프 여부
    bool bLoopAnimation;

    // 마지막 프레임 도달 여부
    bool bReachedEnd;
};
```

---

# 🟦 2. 클래스 핵심 역할 요약

|역할|설명|
|---|---|
|**단일 애니메이션 시퀀스 재생기**|Sequence를 시간에 따라 재생|
|**Update 단계에서 CurrentTime 증가**|DeltaSeconds × PlayRate 반영|
|**Evaluate 단계에서 Sequence Pose 추출(Sample)**|해당 시간의 LocalPose 계산|
|**Loop / Non-Loop 처리**|애니메이션 끝났을 때 어떻게 행동할지 지정|
|**PlayRate / Position 제어**|BlendSpace나 StateMachine 입력으로 활용됨|

---

# 🟦 3. 기능별 상세 설명 (메서드 + 반환형)

---

# 🔷 A. Update Phase (재생 시간 진행)

## ✔ **`void Update_AnyThread(const FAnimationUpdateContext& Context)`**

**반환형:** void  
**역할:**

- DeltaSeconds × PlayRate 만큼 CurrentTime 증가
    
- AdvanceTime() 호출
    
- Loop 처리 또는 End 처리
    
- 노티파이의 FireTimeRange 업데이트
    

StateMachine 내부에서 Active State가 이 SequencePlayer를 가지고 있을 경우 Update가 호출됨.

---

## ✔ **`float AdvanceTime(float DeltaTime)`**

**반환형:** float (증가된 시간)  
**역할:**

- PlayRate를 곱하여 재생 시간 증가
    
- Loop 또는 Clamp 처리
    
- 최종 증가량 반환
    

예:

```
DeltaTime = 0.016
PlayRate = 2.0 → 실제 증가 = 0.032
```

---

# 🔷 B. Evaluate Phase (Pose 계산)

## ✔ **`void Evaluate_AnyThread(FPoseContext& Output)`**

**반환형:** void  
**역할:**

- Sequence에서 현재 CurrentTime의 Pose를 Sample
    
- Output에 Bone Transform 배열로 저장
    
- Curve 값도 함께 Evaluate (MorphTarget 등)
    

이 함수는 “애니메이션의 본 결과를 실제로 계산하는 핵심 함수”.

---

# 🔷 C. Playback Control (재생 제어)

## ✔ **`void SetPlayRate(float NewRate)`**

**반환형:** void  
**역할:** 재생 속도 변경 (부드러운 애니메이션 보간용으로 자주 사용)

---

## ✔ **`void SetPosition(float NewPosition)`**

**반환형:** void  
**역할:**

- CurrentTime을 강제로 설정
    
- 특정 타이밍 스크럽 또는 초기 프레임 정지에 사용
    

---

## ✔ **`float GetCurrentTime() const`**

**반환형:** float  
**역할:** 현재 재생 시간 반환  
Transition Rule 등에서 CurrentTime 기반 조건 체크 가능  
(ex: 특정 State에서 0.5초 지나면 트랜지션)

---

# 🟦 4. 내부 처리 흐름 요약

```
-------------------------
Update Phase
-------------------------
Update_AnyThread()
 → AdvanceTime()
 → Update Notifies
 → Handle Looping

-------------------------
Evaluate Phase
-------------------------
Evaluate_AnyThread()
 → Sequence.Sample(CurrentTime)
 → Fill Output Pose
 → Output.Curves = Sampled Curves
```

---

# 🟦 5. 과제 구현 시 필요한 “최소 버전”

너의 게임 엔진 프로젝트에도 적용하려면  
SequencePlayer의 핵심 기능은 아래 네 가지다:

1. **CurrentTime 관리**
    
2. **PlayRate 적용**
    
3. **Loop 처리**
    
4. **Sequence Sample → Pose 생성**
    

이것만 구현하면 사실상 완전한 단일 애니메이션 플레이어가 된다.

---

# 🟦 6. 요약 (가장 중요한 5줄)

- **FAnimNode_SequencePlayer는 하나의 애니메이션을 재생하는 가장 기본 노드이다.**
    
- Update에서 CurrentTime 증가, Evaluate에서 Pose 샘플링을 수행한다.
    
- PlayRate, Position, Loop 기능을 포함한다.
    
- Notify Range도 Update 단계에서 처리된다.
    
- StateMachine과 Blend 노드의 기초 구성 요소가 되는 핵심 노드이다.
    
