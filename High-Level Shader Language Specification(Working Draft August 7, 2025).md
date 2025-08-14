---
tags:
  - language/hlsl
---

_들어가는 말_

---

# 1 Introduction

==1==    The High Level Shader Language(HLSL) is the GPU programming language provided in conjunction with the DirectX runtime.

==1==    고수준 쉐이더 언어(HLSL)는 DirectX 런타임과 함께 제공되는 GPU 프로그래밍 언어이다.

Over many years its use has expanded to cover every major rendering API across all major development platforms.

수년에 걸쳐 그 사용 범위가 확장되어 모든 주요 개발 플랫폼의 모든 주요 렌더링 API를 포괄하게 되었다.

Despite its polularity and long history HLSL has never had a formal language specification.

그 중요성과 오랜 역사에도 불구하고 HLSL은 그동안 공식적인 언어 명세서를 가지지 않았다.

This document seeks to change that.

이 문서는 이러한 점을 바꿔보고자 한다.

==2==    HLSL draws heavy inspiration originally from ISO C standard (2011) and later from ISO C++ standard (2011) with additions specific to graphics and parellel computation programming.

==2==    HLSL은 ISO C 표준(2011)과 ISO C++ 표준(2011)로부터 강력하게 영감을 받았으며 그래픽과 병렬 연산 프로그래밍에 특화된 사항들이 추가되었다.

The language is also influenced to a lesser degree by other polular graphics and parellel programming languages.

이 언어는 또한 다른 유명한 그래픽 및 병렬 프로그래밍 언어들에 의해서도 더 적은 정도로 영향받았다.

==3==    HLSL has two reference implementations which this specification draws heavily from.

HLSL은 이 명세서가 많은 부분을 참조하는 두 개의 참조를 가지고 있다.

The original reference implementation Legacy DirectX Shader Compiler (FXC) has been in use since DirectX 9.

원래의 참조인 구형 DirectX 쉐이더 컴파일러 (FXC)는 DirectX 9부터 사용되어 왔다.

The more recent reference implementation DirectX Shader Compiler (DXC) has been the primary shader compiler since DirectX 12.

더 최근의 참조인 DirectX 쉐이더 컴파일러 (DXC)는 DirectX 12부터 주된 쉐이더 컴파일러로 자리잡았다.

==4==    In writing this specification bias is leaned toward the language behavior of DXC rather than the behavior of FXC, although that can vary by context.

==4==    이 명세서를 작성함에 있어서 편향은 FXC의 동작보다는 DXC의 언어 동작 쪽으로 기울어져 있으나, 이는 상황에 따라 달라질 수 있다.

==5==    In very rare instances this spec will be aspirational, and may diverge from both reference implementation behaviors.

==5==    매우 드문 경우에 이 명세서는 이상적인 목표를 제시할 수 있으며, 두 참조의 동작 모두에서 벗어날 수 있다.

This will only be done in instance where there is an intent to alter implementation behavior in the future.

이러한 일은 구현된 동작을 미래에 대체할 의도가 있을 때에만 일어날 것이다.

Since this document and the implementations are living sources, one or the other may be ahead in different regards at any point in time.

이 문서와 앞서 언급한 참조들은 계속 발전하는(갱신되는) 자료이므로, 어느 시점에서든 서로 다른 측면에서 한쪽이 다른 쪽보다 앞서 있을 수 있다.

# 1.1 Scope

==1==    This document specifies the requirements for implementations of HLSL.

이 문서는 HLSL의 구현에 대한 요구사항들을 명시한다.

The HLSL specification is based on and highly influenced by the specifications for the C Programming Language (C) and the C++ Programming Language (C++)

HLSL 명세서는 C와 C++ 프로그래밍 언어의 명세서에 기반하며 많은 영향을 받았다.

==2==    This document covers both describing the language grammar and semantics for HLSL, and (in later sections) the standard library of data types used in shader programming.



