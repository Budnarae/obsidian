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

## 1.1 Scope

==1==    This document specifies the requirements for implementations of HLSL.

이 문서는 HLSL의 구현에 대한 요구사항들을 명시한다.

The HLSL specification is based on and highly influenced by the specifications for the C Programming Language (C) and the C++ Programming Language (C++)

HLSL 명세서는 C와 C++ 프로그래밍 언어의 명세서에 기반하며 많은 영향을 받았다.

==2==    This document covers both describing the language grammar and semantics for HLSL, and (in later sections) the standard library of data types used in shader programming.

==2==    이 문서는 HLSL의 언어 문법과 의미론을 설명하는 것과 (이후 목차에서) 셰이더 프로그래밍에서 사용되는 데이터 타입들의 표준 라이브러리 모두를 다룬다. 

## 1.2 Normative References

The following referenced documents provide significant influence on this document and should be used in conjunction with interpreting this standard.

다음 참조 문서들은 이 문서에 상당한 영향을 제공하며, 이 표준을 해석하는 데 있어서 함께 사용되어야 한다.

- ISO C standard (2011), Programming languages - C
- ISO C++ standard (2011), Programming languages - C++
- [DirectX Specifications](https://microsoft.github.io/DirectX-Specs/)

## 1.3 Terms and definitions

==1==    This document aims to use terms consistent with their definitions in ISO C standard (2011) and ISO C++ standard (2011).

==1==    이 문서는 ISO C 표준(2011)과 ISO C++ 표준(2011)에서의 정의와 일치하는 용어를 사용하는 것을 목표로 한다.

In cases where the definitions are unclear, or where this document diverges from ISO C standard (2011) and ISO C++ standard (2011), the definitions in this section, the remaining sections in this chapter, and the attached glossary (13) supersede other sources.

정의가 불분명한 경우나 이 문서가 ISO C 표준(2011) 및 ISO C++ 표준(2011)에서 벗어나는 경우, 이 섹션, 이 장의 나머지 섹션들, 그리고 첨부된 용어집(13)의 정의가 다른 출처들을 대체한다.

## 1.4 Common Definitions

==1==    The following definitions are consistent between HLSL and the ISO C standard (2011) and ISO C++ standard (2011) specifications, however they are included here for reader convenience.

다음의 정의들은 HLSL, ISO C 표준 (2011) 그리고 ISO C++ 표준 (2011) 명세서에서 일관되게 사용되지만, 독자의 편의를 위해 아래에 별첨한다.

### 1.4.1 Correct Data

==1==    Data is correct if it represents values that have specified or unspecified but not undefined behavior for all the operations in which it is used.

==1==    데이터가 사용되는 모든 연산에서 정의되지 않은 동작이 아닌 명시된 또는 명시되지 않은 동작을 가지는 값들을 나타낸다면, 그 데이터는 올바르다.

Data that is the result of undefined behavior is not correct, and may be treated as undefined.

정의되지 않은 동작의 결과인 데이터는 올바르지 않으며, 정의되지 않은 것으로 취급될 수 있다.

### 1.4.2 Diagnostic Message

==1==    An implementation define message belonging to a subset of the implementation's output messages which communicates diagnostic information to the user.

==1==    구현체에서 정의한 메시지로, 구현체의 출력 메시지의 부분집합에 속하며 사용자에게 진단 정보를 전달한다.

### 1.4.3 Ill-formed Program

==1==    A program that is not well-formed, for which the implementation is expected to return unsuccessfully and produce one or more diagnostic messages.

==1==    성공적으로 반환하지 못하고 하나 이상의 경고 메시지를 출력할 것으로 예상되는 잘 짜여지지 못한 프로그램이다.

### 1.4.4 Implementation-defined Behavior

==1==    Beha