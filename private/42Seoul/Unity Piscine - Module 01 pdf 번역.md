---
tags: 
  - 42_outer_subject
---
---

# Piscine Unity - Module01

피신 유니티 - 모듈01

3D physics, Tags, Layers and Scene

3D 물리, 태그, 레이어 그리고 씬

Summary: In this document, you will find the Module01 subject of the Unity Piscine.

요약: 이 문서에서는 유니티 피신의 Module01 주제를 찾을 수 있습니다.

Version: 1.00

버전: 1.00

# Contents

목차

I Instructions
II Foreword
III Exercise 00: Thomas and his friends 
IV Exercise 01: Exit this way!
V Exercise 02: Stage2!
VI Exercise 03: Interactivity
VII Exercise 04: Buttons!
VIII Exercise 05: A deadly game!
IX Submission and peer-evaluation

I 지침 2
II 서문 3
III 연습문제 00: 토마스와 친구들 4
IV 연습문제 01: 이쪽으로 나가세요! 6
V 연습문제 02: 스테이지2! 8
VI 연습문제 03: 상호작용성 9
VII 연습문제 04: 버튼들! 10
VIII 연습문제 05: 치명적인 게임! 11
IX 제출 및 동료 평가 12

# I - Instructions

(생략)

# II - Foreword

서문

Today's starring :

오늘의 주연 :

• Thomas - Lonely and slightly naive, Thomas likes to list his observations about the world - and is absolutely fantastic at falling.

• 토마스 - 외롭고 약간 순진하며, 세상에 대한 자신의 관찰을 나열하기를 좋아하고 - 넘어지는 데는 정말 환상적입니다.

• Chris - Pessimistic, irritable and suspicious - Chris might not be the best jumper, but he was doing just fine on his own.

• 크리스 - 비관적이고, 짜증을 잘 내며 의심이 많습니다 - 크리스는 최고의 점퍼는 아닐지 모르지만, 혼자서도 잘 해내고 있었습니다.

• John - Rather proud of his agility and sportiness, John quite likes an audience so decides to look after Thomas and Chris.

• 존 - 자신의 민첩함과 운동 신경에 꽤 자부심을 느끼며, 관객을 꽤 좋아해서 토마스와 크리스를 돌보기로 결정합니다.

• Claire - Claire lacks confidence, she moves slowly and considers herself rubbish at jumping.

• 클레어 - 클레어는 자신감이 부족하고, 느리게 움직이며 점프를 못한다고 생각합니다.

But then she discovers that she might be a superhero.

하지만 그때 그녀는 자신이 슈퍼히어로일지도 모른다는 것을 발견합니다.

• Laura - Laura isn't great at jumping, although she does have her own unique ability - which, sadly, she's too ashamed to tell anyone about.

• 로라 - 로라는 점프를 잘하지 못하지만, 자신만의 독특한 능력을 가지고 있습니다 - 안타깝게도, 그녀는 너무 부끄러워서 아무에게도 말하지 못합니다.

An ominous pixel cloud has been following her around lately, and this worries the others.

최근 불길한 픽셀 구름이 그녀를 따라다니고 있으며, 이는 다른 이들을 걱정하게 합니다.

• James - James had always been different.

• 제임스 - 제임스는 항상 달랐습니다.

Not least because of his unique disregard for Newtonian laws.

특히 뉴턴 법칙에 대한 그의 독특한 무시 때문입니다.

• Sarah - On a quest to find the fountain of knowledge and learn the truth about her world, Sarah sees herself as rather more intelligent than the other "lesser" quadrilaterals.

• 사라 - 지식의 샘을 찾고 그녀의 세계에 대한 진실을 배우려는 여정에서, 사라는 다른 "하급" 사각형들보다 자신이 꽤 더 지능적이라고 생각합니다.

# III - Exercise 00: Thomas and his friends

연습문제 00: 토마스와 친구들

Exercise:

연습문제:

Exercise 00: Thomas and his friends

연습문제 00: 토마스와 친구들

Turn-in directory: unityModule01

제출 디렉토리: unityModule01

Required elements: The "Stage1" scene, PlayerController scripts on each character and anything relevant

필수 요소: "Stage1" 씬, 각 캐릭터의 PlayerController 스크립트 및 관련된 모든 것

Forbidden functions: None

금지된 기능: 없음

! Demo: Take inspiration from it if you wish, but keep in mind that is only demonstration and some behaviours do not necessarily correspond with the desired behaviour in these exercices.

! 데모: 원한다면 여기서 영감을 얻으세요, 하지만 이것은 단지 시연일 뿐이며 일부 동작은 이 연습문제에서 요구하는 동작과 반드시 일치하지 않을 수 있다는 점을 명심하세요. (원문 오타 수정: exercises)

To start, run the demo so you know where you going today.

시작하려면, 오늘 어디로 가는지 알 수 있도록 데모를 실행하세요. (원문 오타 수정: you're going)

Create a scene Stage1 with:

다음 요소들을 포함하는 Stage1 씬을 만드세요:

• A Ground.

• 땅(Ground).

• A Camera.

• 카메라(Camera).

• 3 characters: Claire, John and Thomas.

• 3명의 캐릭터: 클레어, 존, 토마스.

At the start no character is active.

시작 시에는 어떤 캐릭터도 활성화되어 있지 않습니다.

You can activate and switch it with the Alpha1, Alpha2 and Alpha3 keys.

Alpha1, Alpha2, Alpha3 키로 캐릭터를 활성화하고 전환할 수 있습니다.

Characters must help each other to pass the levels!

캐릭터들은 레벨을 통과하기 위해 서로 도와야 합니다!

You can move the characters right and left with the keyboard (AD keys) and press the space bar to jump.

키보드(AD 키)로 캐릭터를 좌우로 움직이고 스페이스 바를 눌러 점프할 수 있습니다.

The camera is automatically centered on the active character.

카메라는 자동으로 활성화된 캐릭터에 중앙 정렬됩니다.

You must be able to reset the scene pressing a key, R and/or Backspace

R 키 또는 Backspace 키를 눌러 씬을 리셋할 수 있어야 합니다.

! Warning! You must only create ONE single script that will be applied to all characters.

! 경고! 모든 캐릭터에 적용될 단 하나의 스크립트만 생성해야 합니다.

You're free to create other independent scripts, to manage the camera or for instance.

카메라 관리 등을 위해 다른 독립적인 스크립트를 자유롭게 생성할 수 있습니다.

# IV - Exercise 01: Exit this way!

연습문제 01: 이쪽으로 나가세요!

Exercise:

연습문제:

Exercice 01: Exit this way!

연습문제 01: 이쪽으로 나가세요! (원문 오타: Exercise)

Turn-in directory: unityModule01

제출 디렉토리: unityModule01

Required elements: The "Stage1" scene, and anything relevant

필수 요소: "Stage1" 씬 및 관련된 모든 것

Forbidden functions: None

금지된 기능: 없음

Now, the characters must also possess different features:

이제 캐릭터들은 다음과 같은 다른 특징들도 가져야 합니다:

• Claire, the blue square moves slower and jumps lower than the others.

• 클레어, 파란색 사각형은 다른 캐릭터들보다 느리게 움직이고 낮게 점프합니다.

• John, the yellow stick moves faster and jumps higher than the others.

• 존, 노란색 막대기는 다른 캐릭터들보다 빠르게 움직이고 높게 점프합니다.

• Thomas stands between both with an average speed and jump capacity.

• 토마스는 평균 속도와 점프 능력으로 둘 사이에 위치합니다.

! You must always use the same script for all your characters

! 모든 캐릭터에 항상 동일한 스크립트를 사용해야 합니다.

They must not be able to jump several times without falling on a surface, ground or other character.

캐릭터들은 표면, 땅 또는 다른 캐릭터 위에 떨어지지 않고 여러 번 점프할 수 없어야 합니다.

No infinite jump or wall jump!

무한 점프나 벽 점프는 안 됩니다!

They must run through a first stage that forces them to cooperate to get to the exit.

캐릭터들은 출구에 도달하기 위해 협력해야 하는 첫 번째 스테이지를 통과해야 합니다.

The exit of each character is indicated by an outline representing them.

각 캐릭터의 출구는 그들을 나타내는 외곽선으로 표시됩니다.

When each character is aligned on their exit, the stage is over.

각 캐릭터가 자신의 출구에 정렬되면 스테이지가 종료됩니다.

You must display a message stating it.

이를 알리는 메시지를 표시해야 합니다.

For the moment, a simple message in the console will be enough.

현재로서는 콘솔에 간단한 메시지를 표시하는 것으로 충분합니다.

The stage must force cooperation, so characters must not be able to reach the exit without the others.

스테이지는 협력을 강제해야 하므로, 캐릭터들은 다른 캐릭터들 없이 출구에 도달할 수 없어야 합니다.

# V - Exercise 02: Stage2!

연습문제 02: 스테이지2!

Exercise:

연습문제:

Exercise 02: Stage2!

연습문제 02: 스테이지2!

Turn-in directory: unityModule01

제출 디렉토리: unityModule01

Required elements: "Stage2" scenes and anything relevant

필수 요소: "Stage2" 씬 및 관련된 모든 것

Forbidden functions: None

금지된 기능: 없음

You must create a second Stage using Physics Layers in the level design:

레벨 디자인에서 물리 레이어(Physics Layers)를 사용하여 두 번째 스테이지를 만들어야 합니다:

• Platforms are either white either a character's color.

• 플랫폼은 흰색이거나 캐릭터의 색상입니다.

• Characters can only use white or their color's platforms.

• 캐릭터는 흰색 플랫폼 또는 자신의 색상 플랫폼만 사용할 수 있습니다.

They go through the others.

다른 색상의 플랫폼은 통과합니다.

• You must link the stages.

• 스테이지들을 연결해야 합니다.

When the characters finish a stage, they have to move to the next stage.

캐릭터들이 스테이지를 끝내면, 다음 스테이지로 이동해야 합니다.

If there are no more stage, they have to go back to the first stage.

더 이상 스테이지가 없으면, 첫 번째 스테이지로 돌아가야 합니다.

# VI - Exercise 03: Interactivity

연습문제 03: 상호작용성

Exercise:

연습문제:

Exercice 03: Interactivity

연습문제 03: 상호작용성 (원문 오타: Exercise)

Turn-in directory: unityModule01

제출 디렉토리: unityModule01

Required elements: "Stage3" scene and anything relevant

필수 요소: "Stage3" 씬 및 관련된 모든 것

Forbidden functions: None

금지된 기능: 없음

It's about to get interesting!

이제 흥미로워질 차례입니다!

Create a Stage3 with teleporters and moving platforms.

텔레포터와 움직이는 플랫폼이 있는 Stage3를 만드세요.

You will choose to create fast and technical pathways, sadistic elevators, like in a good old retro game where it will take 10 seconds to get the right elevator alignment.

빠르고 기술적인 경로, 가학적인 엘리베이터(예: 올바른 엘리베이터 정렬에 10초가 걸리는 오래된 레트로 게임처럼)를 만들도록 선택할 것입니다.

The goal is to create a pleasant level to run through, not just a demonstration of virtuosity.

목표는 단순히 기교를 과시하는 것이 아니라, 즐겁게 통과할 수 있는 레벨을 만드는 것입니다.

Don't forget to progressively add your levels to the build.

빌드에 점진적으로 레벨을 추가하는 것을 잊지 마세요.

# VII - Exercise 04: Buttons!

연습문제 04: 버튼들!

Exercise :

연습문제 :

Exercise 04: Buttons!

연습문제 04: 버튼들!

Turn-in directory: unityModule01

제출 디렉토리: unityModule01

Required elements : "Stage4" scene and anything relevant

필수 요소 : "Stage4" 씬 및 관련된 모든 것

Forbidden functions: None

금지된 기능: 없음

Now, create a Stage4 with switches that open doors.

이제 문을 여는 스위치가 있는 Stage4를 만드세요.

Even better, color switches that open color doors.

더 좋게는, 색깔 문을 여는 색깔 스위치입니다.

Better yet!

더욱 좋습니다!

White switches take the color of the character that activates them and open the matching color doors

흰색 스위치는 활성화하는 캐릭터의 색상을 띠고 해당 색상의 문을 엽니다.

Finally, switches that change the platform colors so the path the characters can use.

마지막으로, 캐릭터가 사용할 수 있는 경로를 위해 플랫폼 색상을 변경하는 스위치입니다.

You're clearly free to design this level as you like as long as you set buttons that work as described above.

위에 설명된 대로 작동하는 버튼을 설정하는 한, 이 레벨을 원하는 대로 자유롭게 디자인할 수 있습니다.

# VIII - Exercise 05: A deadly game!

연습문제 05: 치명적인 게임!

Exercise:

연습문제:

Exercise 05: A deadly game!

연습문제 05: 치명적인 게임!

Turn-in directory: unityModule01

제출 디렉토리: unityModule01

Required elements: "Stage5" scene and anything relevant

필수 요소: "Stage5" 씬 및 관련된 모든 것

Forbidden functions: None

금지된 기능: 없음

For the last Stage5, we're going to set the difficulty a little higher so the player doesn't have the feeling they're just walking around:

마지막 Stage5에서는 플레이어가 단순히 돌아다니고 있다는 느낌을 받지 않도록 난이도를 약간 높일 것입니다:

• Create color turrets that shoot regularly.

• 정기적으로 발사하는 색깔 터렛을 만드세요.

The shot only hits the same color characters.

발사된 탄환은 같은 색깔의 캐릭터만 맞춥니다.

• Create traps on the ground or in the air.

• 땅이나 공중에 함정을 만드세요.

• Create holes.

• 구멍을 만드세요.

The camera will not follow a character falling in a hole.

카메라는 구멍에 빠지는 캐릭터를 따라가지 않습니다.

• If a character is hit by a turret shot, hits a trap or falls in a hole, the game is over.

• 캐릭터가 터렛 탄환에 맞거나, 함정에 부딪히거나, 구멍에 빠지면 게임은 종료됩니다.

You can code everything with yesterday's and today's lessons.

어제와 오늘의 레슨 내용으로 모든 것을 코딩할 수 있습니다.

Don't use any other system, especially with timed actions and coroutines to manage the turrets' shots.

특히 터렛 발사를 관리하기 위해 시간 제한 액션이나 코루틴과 같은 다른 시스템을 사용하지 마세요.

We'll see about that later.

그것에 대해서는 나중에 알아볼 것입니다.

# IX - Submission and peer-evaluation

제출 및 동료 평가

Turn in your assignment in your Git repository as usual.

평소대로 당신의 과제를 Git 저장소에 제출하세요.

Only the work inside your repository will be evaluated during the defense.

방어(defense) 중에는 당신의 저장소 내의 작업물만 평가될 것입니다.

Don't hesitate to double check the names of your folders and files to ensure they are correct.

폴더와 파일 이름이 올바른지 확인하기 위해 주저하지 말고 다시 확인하세요.

! You should not put all the files of a project on git, otherwise the disk space occupied by the repository will be unnecessarily increased.

! 프로젝트의 모든 파일을 git에 올리면 안 됩니다. 그렇지 않으면 저장소가 차지하는 디스크 공간이 불필요하게 증가합니다.

Here is how to configure Unity and GIT for an optimal use.

최적의 사용을 위해 Unity와 GIT를 설정하는 방법은 다음과 같습니다.

• Make sure that Unity saves as many files as possible in text form instead of binary.

• Unity가 가능한 한 많은 파일을 바이너리 대신 텍스트 형식으로 저장하도록 하세요.

In Unity, go to Edit >Project Settings > Editor.

Unity에서 Edit > Project Settings > Editor로 이동하세요.

Under textttAsset Serialization, you have to choose the Force Text Mode.

Asset Serialization(원문 OCR 오류 수정) 아래에서 Force Text 모드를 선택해야 합니다.

• check that the .gitignore file automatically generated by unity is present.

• unity에 의해 자동으로 생성된 .gitignore 파일이 있는지 확인하세요.

i The evaluation process will happen on the computer of the evaluated group.

i 평가 과정은 평가받는 그룹의 컴퓨터에서 진행될 것입니다.