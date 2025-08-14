---
tags:
  - language/hlsl
---

_들어가는 말_

---

# Introduction

==1==    The High Level Shader Language(HLSL) is the GPU programming language provided in conjunction with the DirectX runtime.

==1==    고수준 쉐이더 언어(HLSL)는 DirectX 런타임과 함께 제공되는 GPU 프로그래밍 언어이다.

Over many years its use has expanded to cover every major rendering API across all major development platforms.

수년에 걸쳐 그 사용 범위가 확장되어 모든 주요 개발 플랫폼의 모든 주요 렌더링 API를 포괄하게 되었다.

Despite its polularity and long history HLSL has never had a formal language specification.

그 중요성과 오랜 역사에도 불구하고 HLSL은 그동안 공식적인 언어 명세(정의)를 가지지 않았다.

This document seeks to change that.

이 문서는 이러한 점을 바꿔보고자 한다.

==2==    HLSL draws heavy inspiration originally from ISO C standard (2011) and later from ISO C++ standard (2011) with additions specific to graphics and parellel computation programming.

==2==    HLSL은 ISO C 표준(2011)과 ISO C++ 표준(2011)로부터 강력하게 영감을 받았으며 그래픽과 병렬 연산 프로그래밍에 특화된 사항들이 추가되었다.

The language is also influenced to a lesser degree by other polular graphics and parellel programming languages.

이 언어는 또한 다른 유명한 그래픽 및 병렬 프로그래밍 언어들에 의해서도 더 적은 정도로 영향받았다.

==3==    HLSL has two reference implementations which this specification draws heavily from.


