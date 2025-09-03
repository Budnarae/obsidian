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



In this particle tutorial we will use a single diamond texture and render it hundreds of times each frame to create a colorful diamond waterfall style effect. Additionally, we will also use blending to blend the particles together so that layered particles cumulatively add their color to each other.

Make sure to also read the summary after going over the tutorial as that is where I explain how to expand this basic particle system into a more advanced, robust, and efficient implementation.