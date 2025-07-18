---
tags:
  - directX11
  - translation
---
---

# Summary

In this preliminary tutorial, we will go through the steps necessary to create a Win32 application.

이 예비 튜토리얼에서, 우리는 Win32 응용프로그램을 만들기 위해 필수적인 단계들을 살펴볼 것이다.

We will be setting up an empty window to prepare for Direct3D 10.

우리는 Direct3D 10을 위한 비어있는 창을 설정할 것이다.

==Source==

`(SDK root)\Samples\C++\Direct3D10\Tutorials\Tutorial00`

# Setting Up The Window

Every Windows application requires at least one window object.

모든 윈도우 응용프로그램은 최소 하나의 창 객체를 필요로 한다.

Before even getting to the DIrect3D 10 specifics, our application must have a working window object.

Direct3D 10에 대한 구체적인 내용에 들어가기 전에, 먼저 애플리케이션에 제대로 동작하는 윈도우 객체가 있어야 한다.

Three things are involved:

세가지 요소가 동반된다.

1. register a window class.

