---
tags:
  - game
  - Unreal_Engine
---

_Unreal에서는 animation을 anim이라고 줄여부른다_

---

# 전체 구조

```
USkeletalMeshComponent
        │
        ▼
   UAnimInstance
        │
        ▼
  FAnimNode_StateMachine ──── (State A: FAnimNode_SequencePlayer)
        │
        └──── (State B: FAnimNode_SequencePlayer)
        │
        ▼
   FAnimNode_SequencePlayer
        │
        ▼
   UAnimSequence
        │
        ▼
     USkeleton
```

# UAnimInstance

## 개요

`UAnimInstance`는 SkeletalMeshComponent가 사용하는 **애니메이션 실행 로직의 핵심 컨트롤러**이다.

UAnimInstance는 **AnimGraph**를 실행해서 **StateMachine**의 Play/Blend Nodes를 업데이트하고 최종 Bone Pose를 계산해 SkeletalMeshComponent에 전달한다.

## 기능

### AnimGraph 실행

언리얼의 애니메이션은 모든 플레이·블렌드 로직이 **AnimGraph(FAnimNode_*)** 안에 들어있다.
`UAnimInstance`는 그 AnimGraph를 다음 순서로 실행한다:

```
Update Phase → Evaluate Phase
```

**Update Phase**

시간 흐름에 따라 상태 업데이트.

- StateMachine 트랜지션 평가
- SequencePlayer 시간 업데이트
- Blend 노드 업데이트
- 매 프레임 파라미터 업데이트

```cpp
void UAnimInstance::NativeUpdateAnimation(float DeltaSeconds);
```

→ AnimGraph 내부의 모든 Update()를 호출하는 시작점.

**Evaluate Phase**

최종 Bone Pose 생성.

- 현재 StateMachine의 활성 노드 Evaluate()
- SequencePlayer에서 BonePose 샘플
- 블렌드 처리
- Component Space 변환 (단순화 가능)

```cpp
void UAnimInstance::NativeEvaluateAnimation(FPoseContext& Output);
```

→ 엔진이 최종 Bone Transform 배열을 얻는 단계.

### Animation StateMachine의 Host

AnimGraph에는 StateMachine이 존재하지만,  
StateMachine을 매 프레임 갱신하는 주체는 **UAnimInstance**이다.

`UAnimInstance`는 다음을 관리한다:

- 현재 상태가 무엇인지 유지
- 전환(Transition) 조건 평가
- 스테이트 안의 SequencePlayer 업데이트

즉,

```cpp
StateMachine.ExecuteUpdate()
StateMachine.ExecuteEvaluate()
```

를 UAnimInstance가 실행한다.

### 애니메이션 파라미터 관리 (Speed, IsJumping, Direction 등)

언리얼 블루프린트에서 다음과 같은 변수를 만들 수 있다:

- Speed
- IsFalling
- Direction
- bIsJumping
- AimYaw, AimPitch

이 변수들은 Animation StateMachine의 트랜지션 조건에 쓰인다.

이 파라미터를 업데이트하는 함수가 바로:

```cpp
void UAnimInstance::NativeUpdateAnimation(float DeltaSeconds);
```

과제에서는 여기에 “애니메이션 파라미터 업데이트 로직”을 넣어주면 된다.

_예시_

```cpp
Speed = OwnerCharacter->GetVelocity().Size();
IsInAir = OwnerCharacter->MovementComponent->IsFalling();
```

### Animation Notify 처리

언리얼에서는 애니메이션에 **노티파이**가 추가되면, UAnimInstance가 이를 처리한다:

- 타격 판정
- 발자국 소리
- 이벤트 콜백

### AnimMontage 처리(생략 가능)

공격/스킬 같은 애니메이션 할 때 쓰는 시스템.

- 루트모션
- 섹션 이동
- 몽타주 블렌드

### 네트워크 동기화(Replication) 처리(생략 확정)

언리얼은 애니메이션 상태를 네트워킹하려면 별도 로직이 필요하지만,  
이 역시 `UAnimInstance`가 중심.

## Evaluate란?

Update가 DeltaTIme을 업데이트하고, Transition 조건 확인, Parameter 업데이트 등의 기능 등을 수행한다면 Evaluate는

==현재 활성 상태/SequencePlayer/Blend 노드 등을 실제로 실행하여  
최종 본 변환 배열(Bone Pose)을 만들어내는 단계이다.==

따라서 Evaluate는 **최종 출력 Pose를 만들어내는 함수**이다.

언리얼은 모든 애니메이션 노드가 다음 메서드를 가진다:

```cpp
void Evaluate(FPoseContext& Output)
```

이 Evaluate가 호출되면:

```
SequencePlayer →
애니메이션 샘플링 Blend →
포즈 블렌딩 StateMachine →
현재 Active Node Evaluate 호출
```

그리고 마지막에 FPoseContext.Output이 “현재 캐릭터의 최종 본 포즈 배열”이 된다.

---

# FAnimNode_StateMachine

## 개요

언리얼 애니메이션 그래프 안에 있는 **상태머신 노드**.

주요 역할:

- 현재 State 유지
- Transition 조건 평가 (Update 단계)
- Active State의 AnimGraph 노드를 Evaluate하여 최종 Pose 생성 (Evaluate 단계)

## 기능

### StateMachine Update (Transition 계산)

Update 단계에서는 “현재 State 유지 → 조건 평가 → 전환 여부 체크” 를 수행한다.

#### Transition 조건 평가

```cpp
void Update_AnyThread(const FAnimationUpdateContext& Context)
```
 
**역할:**
- 상태머신의 모든 transition rule을 업데이트함
- 각 State 노드의 Update()도 호출
- Transition 조건(bool) 판단
- 조건 충족 시 Active State 변경

**설명:**  
애니메이션 Update 단계는 게임프레임과 동일하게 호출되며,  
상태머신은 이 시점에 “어떤 State로 넘어가야 하는지”를 결정한다.

---

#### State 변경 로직 내부 함수

```cpp
bool ChangeState(int32 NewStateIndex, const FAnimationUpdateContext& Context)
```

**반환:** bool (전환 성공 여부)  
**역할:**
- 조건 충족 시 새로운 State로 전환
- StateBegin/StateEnd Notify 호출
- Internal State Time 초기화

#### Transition 가능 여부 판단

```
bool CanEnterTransition(int32 TransitionIndex)
```

**반환:** bool  
**역할:** 
- Transition이 가능한지 rule 검사 (Transition Rule 노드에서 계산된 조건 기반)

---

#### Transition Rule 실행

```
bool EvaluateTransition(int32 TransitionIndex, const FAnimationUpdateContext& Context)
```

**반환:** bool  
**역할:**
- Blueprint/Native 애님 그래프에 정의된 Transition Rule 실행
- 조건 결과 반환

---

### StateMachine Evaluate (현재 State의 Pose 생성)

Transition은 Update에서 하고, Evaluate는 실제 Pose를 만든다.

#### **현재 State Evaluate**

### **`void Evaluate_AnyThread(FPoseContext& Output)`**

**반환:** void  
**역할:**

- 현재 활성화된 State의 AnimNode Evaluate 호출
    
- State 노드의 Evaluate 결과를 최종 Pose로 Output에 넣음
    

설명:  
StateMachine 스스로는 Pose를 만들지 않고,  
“현재 State가 가진 Root AnimNode”가 Pose를 만든다.

---

## ✔ **각 State의 blend 처리**

(BlendTransition AnimNode 포함 시) 아래 같은 함수가 내부적으로 호출됨:

### **`void EvaluateTransitionPose(FPoseContext& Output)`**

**반환:** void  
**역할:**

- Transition 중이면
    
    - 이전 State Pose / 새 State Pose / Blend Alpha 기반으로  
        포즈 블렌딩 처리
        

---

# 🟦 3) State Begin / End Notify 처리

상태 전환에 따라 Notify 호출이 발생한다.

---

## ✔ **State 시작**

### **`void OnStateEntered(int32 StateIndex, const FAnimationUpdateContext& Context)`**

**반환:** void  
**역할:**

- StateBegin 애님 노티파이 실행
    
- State 전용 변수 초기화
    

---

## ✔ **State 종료**

### **`void OnStateExited(int32 StateIndex, const FAnimationUpdateContext& Context)`**

**반환:** void  
**역할:**

- StateEnd 애님 노티파이 실행
    

---

# 🟦 4) StateMachine 정보 조회

---

## ✔ **현재 Active State Index 가져오기**

### **`int32 GetCurrentState()`**

**반환:** int32  
**역할:** 현재 활성화된 State index 리턴

---

## ✔ **현재 State 체류 시간**

### **`float GetCurrentStateElapsedTime()`**

**반환:** float  
**역할:**

- 활성 State에 머문 시간
    
- Transition 조건에서 많이 사용됨
    

---

## ✔ **State 갯수**

### **`int32 GetStateCount()`**

**반환:** int32

---

# 🟦 5) Transition Blend 처리

Transition Blend는 중간 블렌드 상태에 있는 애니메이션을 조합하는 부분.

---

## ✔ BlendAlpha 계산

### **`float ComputeTransitionBlendTime(const FAnimationUpdateContext& Context)`**

**반환:** float  
**역할:** Transition 중 현재 blend alpha 반환

---

## ✔ Blend Evaluate

### **`void EvaluateTransition(int32 TransitionIndex, FPoseContext& Output)`**

**반환:** void  
**역할:**

- 이전 State Pose + Target State Pose 조합
    
- Alpha 활용하여 최종 Pose 계산
    

---

# 🟥 Update / Evaluate 처리 순서 (정확한 전체 흐름)

```
Update Phase
------------------------
StateMachine.Update()
 → 각 State.Update()
 → Transition Rule Evaluate()
 → ChangeState()

Evaluate Phase
------------------------
StateMachine.Evaluate()
 → Active State.Evaluate()
 → If Transition: Blend Evaluate()
 → Output = 최종 Pose
```

---

# 🟥 최종 요약

`FAnimNode_StateMachine`은 **Update 단계에서 전환(Transition) 논리를 평가하고**,  
Evaluate 단계에서 **현재 State의 AnimNode를 Evaluate하여 Pose(본 배열)를 생성**한다.

---

원하면 다음 클래스도 같은 형식으로 정리해줄게:

- `FAnimNode_SequencePlayer`
    
- `UAnimSequence`
    
- `USkeleton`
    
- `USkeletalMeshComponent`
    

어떤 것을 다음으로 볼까?