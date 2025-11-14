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

### 요약

`UAnimInstance`는 SkeletalMeshComponent가 사용하는 **애니메이션 실행 로직의 핵심 컨트롤러**이다.

UAnimInstance는 **AnimGraph**를 실행해서 **StateMachine**의 Play/Blend Nodes를 업데이트하고 최종 Bone Pose를 계산해 SkeletalMeshComponent에 전달한다.

### 기능

#### AnimGraph 실행

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
```
void UAnimInstance::NativeUpdateAnimation(float DeltaSeconds);
### 🔹 Update Phase

시간 흐름에 따라 상태 업데이트.

- StateMachine 트랜지션 평가
    
- SequencePlayer 시간 업데이트
    
- Blend 노드 업데이트
    
- 매 프레임 파라미터 업데이트