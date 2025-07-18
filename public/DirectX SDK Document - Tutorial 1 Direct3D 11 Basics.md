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

The first steps of creating the window and message loop are identical in Direct3D 9, Direct3D 10, and DIrectD3 11.

창과 메시지 루프를 만드는 첫번째 단계는 Direct3D 9, 10, 11에서 모두 동일하다.

See DIrect3D 10 Tutorial 00: Win32 Basics for an introduction to this process.

이 단계에 대해 소개한 [[DirectX SDK Document - Tutorial 0 Win32 Basics]]을 보도록 하자.

Now that we have a window that is displaying, we can continue to set up a Direct3D 11 device.

이제 우리는 창을 얻었으므로, 계속해서 Direct3D 11 장치를 설정해보자.

SetUp is necessary if we are going to render any 3D scene.

3차원 장면을 렌더링하는데 설정은 필수적이다.

The first thing to do is to create three objects: a device, an immediate context, and a swap chain.

첫번째로 해야할 일은 3개의 객체를 만드는 것이다: 장치, 즉시 컨텍스트, 스왑 체인.

THe immediate context is a new object in Direct3D 11.

즉시 컨텍스트는 Direct3D 11의 새로운 객체이다.

---

In Direct3D 10, the device object was used to perform both rendering and resource creation.

DIrect3D 10에서, 장치 객체는 렌더링과 리소스 생성을 둘 다 수행했다.

In Direct3D 11, the immeidate context is used by the application to perform rendering onto a buffer, and the device contains methods to create resources.

Direct3D 11에서 즉시 컨텍스트는 응용프로그램이 버퍼에 렌더링할 때 사용하고, 장치는 리소스를 생성하는 메서드를 가진다.

---

The swap chain is responsible for taking the buffer to which the device renders, and displaying the content, on the actual monitor screen.

스왑 체인은 장치가 렌더링한 버퍼를 가져와서 실제 모니터 화면에 내용을 보여주는 역할을 한다.

The swap chain contians two or more buffers, mainly the front and the back.

스왑 체인은 두 개 이상의 버퍼를 포함하는데, 주로 프론트 버퍼와 백 버퍼이다.

These are textures to which the device renders in order to display on the monitor.
