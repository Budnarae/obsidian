---
tags:
  - graphics
  - directX11
  - languages/hlsl
---

_High-level shader language_

---

# 개요

HLSL은 DirectX11의 프로그램 가능한 쉐이더를 짤 때 사용하는 C와 유사한 고수준 쉐이더 언어이다.

예를 들어, HLSL로 정점 쉐이더와 픽셀 쉐이더를 작성하여 DirectX3D 실행 프로그램의 렌더링 기능을 구현하는 데에 사용할 수 있다.

또는 HLSL로 컴퓨트 쉐이더를 작성하여 물리 시뮬레이션을 구현할 수도 있다.

HLSL은 프로그래밍 가능한 3차원 그래픽 파이프라인을 설정하기 위해 사용된다. HLSL을 사용해 전체 파이프라인을 구축할 수도 있다.

# Reference for HLSL

이 문단은 HLSL의 언어적 특성을 설명한다.

## Language Syntax

HLSL 쉐이더는 변수와 함수로 구성되며, 함수는 다시 구문(statement)들로 이루어진다. 이 문단은 다음의 내용을 포함한다.

1. 변수를 정의하고 선언하는 방법.
2. 쉐이더가 실행 시간에 변수에 기반한 결정을 내릴 수 있도록 하는 흐름 제어
3. 