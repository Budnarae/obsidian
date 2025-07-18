---
tags:
  - directX11
  - translation
---
---

# Summary

In this first tutorial, we will go through the elements necessary to create a minimal Direct3D 11 application.

이 튜토리얼에서 우리는 최소한의 Direct3D 11 응용프로그램을 만들기 위해 필수적인 요소를 살펴볼 것이다.

Every Direct3D 11 application must have these elements to function properly.

모든 Direct3D 11 응용프로그램은 제대로 기능하기 위해서 이 요소들이 필요하다.

The elements include setting up a window and a device object, and then displaying a color on the window.

요소는 창이나 장치 객체를 설정하거나, 창에 색깔을 표시하는 것을 포함한다.

==Source==

`(SDK root)\Samples\C++\Direct3D11\Tutorials\Tutorial01`

## Setting up The Direct3D 11 Device

THe first steps of creating the window and message loop are identical in Direct3D 9, DirectX3D 10, 
