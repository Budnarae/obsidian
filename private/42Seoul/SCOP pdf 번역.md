---
tags:
  - 42_outer_subject
---
---

# SCOP

**Basic GPU rendering with OpenGL**

OpenGL을 사용한 기초적인 GPU 렌더링

_Summary : This mini project is a first step towards the use of OpenGL... And other GPU rendering API_

_요약 : 이 미니 프로젝트는 OpenGL 그리고 다른 GPU 렌더링 API를 사용하는 첫 걸음이 될 것입니다._

## Subject

### It does not hurt to feel good.

아픈 건 싫으니까.

Once in a while, it feels good to feel good.

한번에 하나씩, 좋은 게 좋은 거잖아요.

So we are going to create a small app to feel great.

따라서 우리는 성취감을 위해서 작은 응용프로그램을 만들어 볼 겁니다.

This project is also organized for you to use a bit of elbow grease.

이 프로젝트는 당신으로 하여금 약간의 노력을 기울이도록 설계되었습니다.

So we have a few restrictions in place.

따라서 이 과제에는 몇 가지 제약이 존재합니다.

### What you need to do

과제 요구 사항

Your goal is to create a small program that will show a 3D object conceived with a modelization program like Blender.

당신의 목표는 Blender 같은 모델화 프로그램으로 구상한 3차원 객체를 표시하는 작은 프로그램을 만드는 것이 목표입니다.

The 3D object is stored in a .obj file.

3차원 객체는 .obj 파일에 저장됩니다.

You will be at least in charge of parsing to obtain the requested rendering.

당신은 요청된 렌더링을 얻기 위해 약간의 파싱을 해야 할 겁니다.

In a window, your 3D object will be displayed in perspective (which means that what is far must be smaller), rotate on itself around its main symmetrical axis (middle of the object basically...).

창에서, 3차원 객체는 원근법으로 표시되어야 하며(멀리 있는 물체가 작게 보여야 한다는 소리입니다), 중심 대칭축(기본적으로 물체의 중앙을 의미합니다)을 따라서 스스로 회전해야 합니다.

By using various colors, it must be possible to distinguish the various sides.

여러가지 색상을 사용하므로서, 다양한 측면을 구분할 수 있어야 합니다.

The object can be moved on three axis, in both directions.

물체는 3개의 축 위에서 양방향으로 움직일 수 있어야 합니다.

Finally, a texture must be applicable simply on the object when we press a dedicated key, and the same key allows us to go back to the different colors.

종국에는, 지정된 키를 눌렀을 때 텍스처가 객체 위에 간단하게 적용되어야 하며, 같은 키를 다시 눌렀을 때 적용을 해제해야 합니다.

A soft transition between the two is requested.

두 상태 사이는 부드럽게 전환되어야 합니다.

The technical constraints are as follows:

다음의 기술적인 제약들을 지켜야 합니다:

You’re free to use any langages (C / C++ / Rust preferred )

언어적인 제약은 없습니다 (C / C++ / Rust를 권장합니다)

You’re free to choose between OpenGL, Vulkan, Metal and the MinilibX

당신은 OpenGl, Vulkan, Metal 그리고 MinilibX 중 하나를 자유롭게 선택할 수 있습니다(MinilibX는 도대체 왜 끼워넣었으며 DirectX는 왜 유기했는가).

Have a classic Makefile (everything you usually put in there).

정석적인 Makefile이 있어야 합니다 (당신이 사용하는 모든 것은 Makefile 안에 있어야 합니다).

You can use external libraries (other than OpenGL, Vulkan or Metal) ONLY to manage the windows and the events.

당신은 창과 이벤트의 관리를 위해서만 (OpenGL, Vulkan, Metal이 아닌) 외부 라이브러리를 사용할 수 있습니다.

No libraries are allowed to load the 3D object, nor to make your matrixes or to load the shaders.

3차원 객체를 로드하거나, 행렬을 계산하거나, 셰이더를 로드하는 기능을 가진 어떠한 라이브러리도 사용할 수 없습니다.

As this is a program to auto-congratulate ourselves, it is crucial that you can present during defense at least the 42 logo given as resources, turning around its central axis (careful, not around one of its corners), with some shades of gray on the sides and a texture of poneys, kitten or unicorn your choice.

이 프로그램은 우리 스스로를 격려하기 위한 것이므로, 평가 중에 42 로고를 렌더링하는 것은 중대 사항입니다. 로고는 스스로의 중심축을 기준으로 회전해야 하며(로고의 모서리를 기준으로 회전하면 안된다는 사실에 유의하세요), 측면을 회색으로 칠해야하며 당신의 선택에 따라 조랑말, 새끼 고양이, 또는 유니콘 중 하나의 텍스처를 매핑할 수 있어야 합니다.

**During the defense, naturally more 3D objects will be tested.**

**평가 동안, 당연히 더 많은 3차원 객체를 테스트하게 됩니다.**

### Bonus

Here are a few ideas of bonuses:

보너스:

The correct management of some ambiguous .obj files, concave, non coplanar...

애매한 .obj 파일, 오목한 형태, 동일 평면에 있지 않은 형태 등을 올바르게 처리하는 것이 중요합니다.

The teapot given with as resources exists in two versions:

주어진 찻주전자 리소스는 두 가지 버전으로 존재합니다:

The first is the original, with some strange border effects.

첫번째는 이상한 테두리 효과가 적용된 원본입니다

The second is an import-export in Blender, with no human touch, but normalized a little by the program.

두번째는 블렌더에서 가져오고 내보내기 한 것으로, 사람의 조작이 가해지지 않고, 프로그램에 의해 약간 정규화되었습니다.

It’s about rendering correctly the first version.

첫번째 버전을 정확히 렌더링하는 것이 조건입니다.

A more subtle application of the texture.

텍스처를 더 절묘하게 적용하세요.

It cannot be stretched on any of the sides

어느 측면에서도 텍스처가 늘어나서는 안됩니다.

There’s got to be more bonuses that you can implement.

당신이 구현할 수 있는 보너스가 추가적으로 있을 것입니다.