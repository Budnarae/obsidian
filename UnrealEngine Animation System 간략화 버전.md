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

#### Animation StateMachine의 Host

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

#### 애니메이션 파라미터 관리 (Speed, IsJumping, Direction 등)

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

#### Animation Notify 처리

언리얼에서는 애니메이션에 **노티파이**가 추가되면, UAnimInstance가 이를 처리한다:

- 타격 판정
- 발자국 소리
- 이벤트 콜백

#### AnimMontage 처리(생략 가능)

공격/스킬 같은 애니메이션 할 때 쓰는 시스템.

- 루트모션
- 섹션 이동
- 몽타주 블렌드

#### 네트워크 동기화(Replication) 처리(생략 확정)

언리얼은 애니메이션 상태를 네트워킹하려면 별도 로직이 필요하지만,  
이 역시 `UAnimInstance`가 중심.

