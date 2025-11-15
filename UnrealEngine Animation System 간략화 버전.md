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

## UAnimInstance

### 개요요

`UAnimInstance`는 SkeletalMeshComponent가 사용하는 **애니메이션 실행 로직의 핵심 컨트롤러**이다.

UAnimInstance는 **AnimGraph**를 실행해서 **StateMachine**의 Play/Blend Nodes를 업데이트하고 최종 Bone Pose를 계산해 SkeletalMeshComponent에 전달한다.

### 기능

#### AnimGraph 실행

언리얼의 애니메이션은 모든 플레이·블렌드 로직이 **AnimGraph(FAnimNode_*)** 안에 들어있다.
`UAnimInstance`는 그 AnimGraph를 다음 순서로 실행한다:

```
Update Phase → Evaluate Phase
```
요

언리얼 애니메이션 그래프 안에 있는 **상태머신 노드**.

주요 역할:

- 현재 State 유지
    
- Transition 조건 평가 (Update 단계)
    
- Active State의 AnimGraph 노드를 Evaluate하여 최종 Pose 생성 (Evaluate 단계)
    

---

# 🟦 1) StateMachine Update (Transition 계산)

Update 단계에서는 “현재 State 유지 → 조건 평가 → 전환 여부 체크” 를 수행한다.

---

## ✔ **Transition 조건 평가**

### **`void Update_AnyThread(const FAnimationUpdateContext& Context)`**

**반환:** void  
**역할:**

- 상태머신의 모든 transition rule을 업데이트함
    
- 각 State 노드의 Update()도 호출
    
- Transition 조건(bool) 판단
    
- 조건 충족 시 Active State 변경
    

**설명:**  
애니메이션 Update 단계는 게임프레임과 동일하게 호출되며,  
상태머신은 이 시점에 “어떤 State로 넘어가야 하는지”를 결정한다.

---

## ✔ **State 변경 로직 내부 함수**

### **`bool ChangeState(int32 NewStateIndex, const FAnimationUpdateContext& Context)`**

**반환:** bool (전환 성공 여부)  
**역할:**

- 조건 충족 시 새로운 State로 전환
    
- StateBegin/StateEnd Notify 호출
    
- Internal State Time 초기화
    

---

## ✔ **Transition 가능 여부 판단**

### **`bool CanEnterTransition(int32 TransitionIndex)`**

**반환:** bool  
**역할:** Transition이 가능한지 rule 검사  
(Transition Rule 노드에서 계산된 조건 기반)

---

## ✔ **Transition Rule 실행**

### **`bool EvaluateTransition(int32 TransitionIndex, const FAnimationUpdateContext& Context)`**

**반환:** bool  
**역할:**

- Blueprint/Native 애님 그래프에 정의된 Transition Rule 실행
    
- 조건 결과 반환
    

---

# 🟦 2) StateMachine Evaluate (현재 State의 Pose 생성)

Transition은 Update에서 하고, Evaluate는 실제 Pose를 만든다.

---

## ✔ **현재 State Evaluate**

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