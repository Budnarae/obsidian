---
tags:
  - directX11
  - translation
---

_rain, fire, smoke..._

---

This tutorial will cover how to create particle systems in DirectX 11 using HLSL and C++.

이번 튜토리얼은 DirectX11에서 HLSL과 C++을 사용해서 파티클 시스템을 생성하는 법을 다룬다.

Particles are usually made by using a single texture placed on a quad.

파티클은 주로 쿼드에 놓여진 하나의 텍스처를 사용하여 만든다.

And then that quad is rendered hundreds of times each frame using some basic physics to mimic things such as snow, rain, smoke, fire, foliage, and numerous other systems that are generally made up of many small but similar elements.

그리고 그 쿼드는 하나의 프레임 당 몇백번이 넘게 렌더링된다. 파티클은 기초적인 물리학을 적용하여 구현되는데, 눈, 비, 연기, 불, 나뭇잎, 그리고 일반적으로 많고 서로 유사하고 미세한 입자로 구성되어 있는 다른 시스템을 모사하기 위해서이다.

In this particle tutorial we will use a single diamond texture and render it hundreds of times each frame to create a colorful diamond waterfall style effect.

이번 파티클 튜토리얼에서 우리는 하나의 다이아몬드 텍스처를 사용할 것이다. 그리고 그것을 각 프레임 당 수백번 렌더링하여 다채로운 색상의 다이아몬든 폭포 효과를 생성할 것이다.

Additionally, we will also use blending to blend the particles together so that layered particles cumulatively add their color to each other.

추가적으로, 우리는 블렌딩도 사용할 것이다. 결과적으로 파티클들은 서로 블렌드 되어 층을 이룬 파티클들이 점증적으로 그들의 색상을 다른 입자에 더할 것이다.

Make sure to also read the summary after going over the tutorial as that is where I explain how to expand this basic particle system into a more advanced, robust, and efficient implementation.

튜토리얼을 모두 살펴본 후에는 요약 부분도 꼭 읽어보세요.
그곳에서 이 기본적인 파티클 시스템을 더 고급스럽고, 견고하며, 효율적인 구현으로 확장하는 방법을 설명하고 있습니다.

# Framework

The framework for this tutorial has the basics as usual.

이번 튜토리얼을 위한 프레임워크는 언제나 그렇듯 기본적인 요소들로 구성된다.

It also uses the TimerClass for timing when to emit new particles.

이번에는 또한 새로운 입자를 방출할 타이밍을 구하기 위한 TimerClass를 사용한다.

The new class used for shading the particles is called ParticleShaderClass.

새로운 클래스인 ParticleShaderClass는 새로운 파티클을 셰이딩하기 위해 사용된다.

And finally, the new particle system itself is encapsulated in the ParticleSystemClass.

그리고 마침내, 새로운 파티클 시스템 그 스스로는 ParticleSystemClass에 의해 캡슐화될 것이다.

![[c4c07faa0ecdbde96ff5dc39933fd87d_MD5.jpeg]]

We will start the code section by looking at the particle shader first.

우리는 파티클 셰이더 코드 부분부터 살펴볼 것이다.

# Part
