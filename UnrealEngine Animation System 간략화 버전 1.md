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


[[UAnimInstance]]
[[FAnimNode_StateMachine]]
[[FAnimNode_SequencePlayer]]
[[UAnimSequence]]