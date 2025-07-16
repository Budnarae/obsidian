---
tags: 
  - 42_outer_subject
---
---

# Unity Piscine - Module00

유니티 피신 - 모듈 00

The basic Unity tools

기본적인 유니티 도구들

Assets, GameObject, Behavior, Input, Transform

에셋, 게임 오브젝트, 동작, 입력, 트랜스폼

# Instructions

If you have problems installing the tools needed for your project on the 42 computers, you can use a virtual machine.

42 컴퓨터에서 프로젝트에 필요한 도구를 설치하는 데 문제가 있다면, 가상 머신을 사용할 수 있습니다.

In this case, you will have to:

이 경우, 다음을 수행해야 합니다:

◦ install the virtual machine software on your computer.

◦ 컴퓨터에 가상 머신 소프트웨어를 설치합니다.

◦ install the operating system of your choice.

◦ 원하는 운영 체제를 설치합니다.

◦ install the tools needed for your project.

◦ 프로젝트에 필요한 도구들을 설치합니다.

◦ Make sure you have the space on your session to install all of this.

◦ 모든 것을 설치할 수 있을 만큼 세션에 공간이 있는지 확인합니다.

◦ You must have everything installed before the evaluation.

◦ 평가 전에 모든 것을 설치해야 합니다.

• Only this page will serve as reference. Do not trust rumors.

• 이 페이지만 참조 자료로 사용하십시오. 루머를 믿지 마십시오.

• Read attentively the whole document before beginning.

• 시작하기 전에 전체 문서를 주의 깊게 읽으세요.

• Your exercises will be corrected by your piscine colleagues.

• 여러분의 연습문제는 piscine 동료들에 의해 수정될 것입니다.

• The document can be relied upon, do not blindly trust the demos or pictures example which can contain not required additions.

• 이 문서는 신뢰할 수 있습니다. 필요하지 않은 추가 항목을 포함할 수 있는 데모나 이미지 예시를 맹목적으로 믿지 마십시오.

• Got a question? Ask your peer on the right. Otherwise, try your peer on the left.

• 질문이 있나요? 오른쪽에 있는 동료에게 물어보세요. 그렇지 않으면 왼쪽에 있는 동료에게 물어보세요.

• By Odin, by Thor! Use your brain !!!

• 오딘의 이름으로, 토르의 이름으로! 머리를 사용하세요!!!

Intra indicates the date and the hour of closing for your repositories.

Intra는 여러분의 저장소가 닫히는 날짜와 시간을 표시합니다.

This date and hour also corresponds to the beginning of the peer-evaluation period for the corresponding piscine day.

이 날짜와 시간은 해당 piscine 날짜의 동료 평가 시작 시간과도 일치합니다.

This peer-evaluation period lasts exactly 24h. 

이 동료 평가 기간은 정확히 24시간 동안 지속됩니다.

After 24h passed, your missing peer grades will be completed with a 0.

24시간이 지난 후, 누락된 동료 평가 점수는 0으로 처리됩니다.

# Introduction

소개

The floor is lava is a game in which players pretend that the floor or ground is made of lava (or any other lethal substance, such as acid or quicksand), and thus must avoid touching the ground, as touching the ground would ¨kill¨the player who did so.

"바닥은 용암이다"는 게임은 플레이어들이 바닥이나 땅이 용암(또는 산이나 유사와 같은 다른 치명적인 물질)으로 만들어졌다고 상상하고, 따라서 땅에 닿는 것을 피해야 합니다. 땅에 닿으면 플레이어가 "죽기" 때문입니다.

The players stay off the floor by standing on furniture or the room’s architecture.

플레이어들은 가구나 방의 구조물 위에 서서 바닥에서 떨어져 있습니다.

The players generally may not remain still, and are required to move from one piece of furniture to the next.

플레이어들은 일반적으로 가만히 있을 수 없으며, 가구에서 다음 가구로 이동해야 합니다.

This is due to some people saying that the furniture is acidic, sinking, or in some other way time-limited in its use.

이는 일부 사람들이 가구가 산성이거나, 가라앉거나, 또는 어떤 식으로든 사용 시간이 제한되어 있다고 말하기 때문입니다.

The game can be played with a group or alone for self amusement.

이 게임은 그룹으로 플레이하거나 혼자서 즐길 수도 있습니다.

There may even be a goal, to which the players must race.

플레이어들이 경쟁해야 할 목표가 있을 수도 있습니다.

The game may also be played outdoors in playgrounds or similar areas.

이 게임은 놀이터나 유사한 지역의 야외에서도 할 수 있습니다.

Players can also set up obstacles such as padded chairs to make the game more challenging.

플레이어들은 게임을 더 어렵게 만들기 위해 패딩 의자와 같은 장애물을 설치할 수도 있습니다.

This is a variation of an obstacle course.

이것은 장애물 코스의 변형입니다.

Typically, any individual can start the game just by shouting ¨The floor is lava!¨

일반적으로, 누구든 "바닥은 용암이다!"라고 외치는 것만으로 게임을 시작할 수 있습니다.

Any player remaining on the floor in the next few seconds is out and can not rejoin the game for some period of time.

다음 몇 초 안에 바닥에 남아 있는 플레이어는 아웃되며 일정 기간 동안 게임에 다시 참여할 수 없습니다.

There often are tasks, items or places that can regenerate lost body parts or health.

잃어버린 신체 부위나 건강을 회복할 수 있는 임무, 아이템 또는 장소가 종종 있습니다.

Depending on the players, these could be embarrassing tasks, or simple things like finding a particular person.

플레이어에 따라 이러한 것들은 당황스러운 임무일 수도 있고, 특정 사람을 찾는 것과 같은 간단한 일일 수도 있습니다.

In one version called ¨Hot Lava Monster¨, sometimes referred to as ¨Skies in the Ringuss¨, usually played on playgrounds, players must stay off the ground (sand, rubber, wood- chips, etc.) and on the play equipment.

"핫 라바 몬스터"라고 불리는 한 버전에서는, 때때로 "Skies in the Ringuss"라고도 불리며, 주로 놀이터에서 플레이되며, 플레이어는 땅(모래, 고무, 나무 조각 등)에서 떨어져 놀이 장비 위에 있어야 합니다.

The person who is playing the ¨monster¨can be on the ¨lava ¨with the objective of attempting to tag another player.

"몬스터" 역할을 하는 사람은 다른 플레이어를 태그하려는 목표를 가지고 "용암" 위에 있을 수 있습니다.

The monster must try to tag or catch the other players.

"몬스터"는 다른 플레이어를 태그하거나 잡으려고 노력해야 합니다.

In some versions, the monster is not allowed to touch certain obstacles, such as wooden platforms or may only touch objects of a certain colour.

일부 버전에서는 "몬스터"가 나무 플랫폼과 같은 특정 장애물을 만질 수 없거나 특정 색상의 물체만 만질 수 있습니다.

The ¨monster ¨must navigate across structures such as across playground slides, monkey bars, ropes courses, etc. instead of the main platform.

"몬스터"는 메인 플랫폼 대신 놀이터 슬라이드, 몽키 바, 로프 코스 등과 같은 구조물을 가로질러 이동해야 합니다.

This game is similar to the traditional children’s game ¨Puss in the Corner¨, or ¨Puss Wants a Corner¨, where children occupying the corner of a room are ¨safe¨, while the Puss, the player who is Ïtïn the middle of the room, tries to occupy an empty corner as the other players dash from one corner to another.

이 게임은 전통적인 어린이 게임인 "구석에 고양이" 또는 "고양이가 구석을 원해"와 유사합니다. 방의 구석을 차지하는 아이들은 "안전"하고, 방 중앙에 있는 "고양이"는 다른 플레이어들이 한 구석에서 다른 구석으로 달려갈 때 빈 구석을 차지하려고 합니다.

This game was often played in school shelter- sheds in Victoria, with the bench-seats along the walls of the shelter-shed being used as platforms joining the corner, while players crossing the floor could be caught by the Puss.

이 게임은 빅토리아의 학교 대피소에서 자주 진행되었으며, 대피소 벽을 따라 있는 벤치 좌석이 구석을 연결하는 플랫폼으로 사용되었고, 바닥을 가로지르는 플레이어는 "고양이"에게 잡힐 수 있었습니다.

# Exercise 00: Floor is Lava

실습 00: 바닥은 용암이다.

| 제출 폴더명 | unityModole00                                                |
| ----------- | ------------------------------------------------------------ |
| 요구 항목   | FloorIsLavaScene 장면, 바닥, 통로 게임 오브젝트와 그 외 기타 |
| 금지 함수   | 없음                                                         |

The purpose of this module is to familiarise you with the different tools provided by Unity.

이 모듈의 목적은 Unity에서 제공하는 다양한 도구에 익숙해지도록 하는 것입니다.

To start create a new 3D project and name it Module00.

시작하려면 새로운 3D 프로젝트를 만들고 이름을 Module00으로 지정하십시오.

An sample scene is already create, you can work directly on it.

샘플 장면이 이미 생성되어 있으므로 바로 작업할 수 있습니다.

Rename this sample scene FloorIsLavaScene.

이 샘플 장면의 이름을 FloorIsLavaScene으로 변경하십시오.

You will only need one scene for all the exercises.

모든 연습에 하나의 장면만 필요합니다.

To create this game you need :

• The floor !
• A pathway.
• A player.
• Some decorations.
• The camera.

이 게임을 만들려면 다음이 필요합니다 :

• 바닥!
• 통로.
• 플레이어.
• 몇 가지 장식.
• 카메라.

Start with the floor:

• Create the Floor GameObject with primitive square.
• Choose its size, (you don’t need it to be big).

바닥부터 시작하십시오 :

• 기본 사각형으로 Floor GameObject를 만드십시오.
• 크기를 선택하십시오 (클 필요는 없습니다).

The Pathway : 

• Create an empty gameObject named Pathway in which you will place all the different GameObjects (stairs, bridges, whatever you want) that will compose your pathway.
• To compose it keep in mind the goal of the game, (move on the pathway without touching the floor).

통로 :

• Pathway라는 이름의 빈 gameObject를 만들고, 그 안에 통로를 구성할 다양한 GameObjects (계단, 다리 등 원하는 모든 것)를 배치합니다.
• 통로를 구성할 때 게임의 목표 (바닥에 닿지 않고 통로 위로 이동)를 염두에 두십시오.

Decoration: Our scene must contain one composed structure (With colors ! because it’s more beautiful), like this tree (this is only an example of a compound structure, you can of course create others):

장식: 우리 장면에는 다음과 같은 트리와 같이 구성된 구조(색상이 있어야 더 아름답기 때문입니다!)가 하나 이상 포함되어야 합니다 (이것은 복합 구조의 예일 뿐이며, 물론 다른 구조를 만들 수도 있습니다).

The Player:

• Your player will look like a ball, so choose carefully the 3D object you create.
• Make it prettier by adding a material with the color/reflection, whatever you want.
• Place it at the beginning of the pathway.
• You will make the moves in the following exercise.

플레이어:

• 플레이어는 공처럼 보일 것이므로, 만들 3D 오브젝트를 신중하게 선택하십시오.
• 색상/반사 등 원하는 재료를 추가하여 더 예쁘게 만드십시오.
• 통로의 시작 부분에 배치하십시오.
• 움직임은 다음 연습에서 만들 것입니다.

And finally, the camera: The main camera is automatically created when the project is created. For this module you will not need to modify it. Simply place it height up so that the player can see the whole pathway.

마지막으로, 카메라: 프로젝트가 생성될 때 메인 카메라는 자동으로 생성됩니다. 이 모듈에서는 수정할 필요가 없습니다. 플레이어가 전체 통로를 볼 수 있도록 높이 올려 배치하기만 하면 됩니다.

# Exercise 01: Path of Exile

실실습 01: 추방의 길

Now that you have your structure and your player, it must be able to move on the path.

이제 구조와 플레이어가 있으므로, 플레이어가 통로 위에서 움직일 수 있어야 합니다.

For this you have to create a script which will be named PlayerController.cs and which will be attached to your player.

이를 위해 PlayerController.cs라는 스크립트를 만들고 플레이어에 연결해야 합니다.

To move, you will have to use the keys WSAD or arrows, both should be possible.

움직이려면 WSAD 키 또는 화살표 키를 사용해야 하며, 둘 다 가능해야 합니다.

Let’s add a little Challenge ! Your player must also be able to jump.

작은 도전을 추가해 봅시다! 플레이어는 점프도 할 수 있어야 합니다.

So, add obstacles on your pathway that the player will have to jump over and of course don’t forget to add the jump to your PlayerController.

따라서 플레이어가 뛰어넘어야 할 장애물을 통로에 추가하고, 물론 PlayerController에 점프 기능을 추가하는 것을 잊지 마십시오.

# Exercise 02: My even more beautiful world

실습 02: 나만의 훨씬 더 아름다운 세계

_You can find here the texture pack from the Unity Asset Store needed for the exercise: Official Unity Asset Store._

_여기에서 연습에 필요한 Unity Asset Store의 텍스처 팩을 찾을 수 있습니다: Official Unity Asset Store._

At the moment, your scene is a little bit dull.

현재 장면은 약간 칙칙합니다.

To remedy this, use the textures from Unity Asset Store to make it a little bit nicer.

이를 개선하기 위해 Unity Asset Store의 텍스처를 사용하여 장면을 조금 더 멋지게 만드십시오.

Make a lava floor, a stone pathway for example or a vegetation obstacles!

예를 들어 용암 바닥, 돌길 또는 초목 장애물을 만드십시오!

In short, let your imagination run wild, but don’t waste too much time either

요컨대, 상상력을 마음껏 발휘하되, 너무 많은 시간을 낭비하지 마십시오.

# Exercise 03: The floor is always lava

실습 03: 바닥은 항상 용암이다.

Now, the heart and the end of the matter.

이제 핵심이자 결론입니다.

The floor is still made of lava!

바닥은 여전히 용암으로 만들어져 있습니다!

So you’ll have to make sure that if your player falls off the pathway, it’s game over.

따라서 플레이어가 통로에서 떨어지면 게임 오버가 되도록 해야 합니다.

For today you don’t need a big title that announces the end.

오늘은 종료를 알리는 큰 제목이 필요하지 않습니다.

Just a small debug.Log that will display Game Over in the console.

콘솔에 Game Over를 표시하는 작은 debug.Log만 있으면 됩니다.

The Player GameObject must also be destroyed when is game over

게임 오버 시 Player GameObject도 파괴되어야 합니다.