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

>**구현체(implementation)란**
>
>특정 표준이나 명세를 실제로 구현한 소프트웨어나 시스템을 의미한다.
>
>**HLSL 맥락에서:**
>
>- **FXC (DirectX Shader Compiler)**: Microsoft의 기존 HLSL 컴파일러
>- **DXC (DirectX Shader Compiler)**: Microsoft의 새로운 HLSL 컴파일러
>- **기타 third-party HLSL 컴파일러들**
>
>**일반적인 예시:**
>
>- **C++ 구현체**: GCC, Clang, MSVC 등
>- **Java 구현체**: Oracle JDK, OpenJDK 등
>- **웹브라우저**: Chrome, Firefox, Safari (각각 HTML/CSS/JS 표준의 구현체)
>
>_출처 : claude_

==3==    HLSL has two reference implementations which this specification draws heavily from.

HLSL은 이 명세서가 많은 부분을 참조하는 두 개의 참조 구현들을 가지고 있다.

The original reference implementation Legacy DirectX Shader Compiler (FXC) has been in use since DirectX 9.

원래의 참조 구현인 구형 DirectX 쉐이더 컴파일러 (FXC)는 DirectX 9부터 사용되어 왔다.

The more recent reference implementation DirectX Shader Compiler (DXC) has been the primary shader compiler since DirectX 12.

더 최근의 참조 구현인 DirectX 쉐이더 컴파일러 (DXC)는 DirectX 12부터 주된 쉐이더 컴파일러로 자리잡았다.

==4==    In writing this specification bias is leaned toward the language behavior of DXC rather than the behavior of FXC, although that can vary by context.

==4==    이 명세서를 작성함에 있어서 편향은 FXC의 동작보다는 DXC의 언어 동작 쪽으로 기울어져 있으나, 이는 상황에 따라 달라질 수 있다.

==5==    In very rare instances this spec will be aspirational, and may diverge from both reference implementation behaviors.

==5==    매우 드문 경우에 이 명세서는 이상적인 목표를 제시할 수 있으며, 두 참조 구현현의 동작 모두에서 벗어날 수 있다.

This will only be done in instance where there is an intent to alter implementation behavior in the future.

이러한 일은 구현체의 동작을 미래에 대체할 의도가 있을 때에만 일어날 것이다.

Since this document and the implementations are living sources, one or the other may be ahead in different regards at any point in time.

이 문서와 앞서 언급한 참조 구현들은 계속 발전하는(갱신되는) 소스이므로, 어느 시점에서든 서로 다른 측면에서 한쪽이 다른 쪽보다 앞서 있을 수 있다.

## 1.1 Scope

==1==    This document specifies the requirements for implementations of HLSL.

이 문서는 HLSL의 구현체에 대한 요구사항들을 명시한다.

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

다음의 정의들은 HLSL, ISO C 표준 (2011) 그리고 ISO C++ 표준 (2011) 명세서에서 일관되게 사용되지만, 읽는 이이의 편의를 위해 아래에 별첨한다.

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

==1==    성공적으로 반환하지 못하고 하나 이상의 경고 메시지를 출력할 것으로 예상되는 올바르지 않은 형태의 프로그램이다.

### 1.4.4 Implementation-defined Behavior

==1==    Behavior of a well-formed program and correct data which may vary by the implementation, and the implementation is expected to document the behavior.

==1==    올바른 형태의 프로그램과 정확한 데이터의 동작이다. 구현체에 따라 달라질 수 있으며, 구현체는 그 동작을 문서화해야 한다.

### 1.4.5 Implementation Limits

==1==    Restrictions imposed upon programs by the implementation of either the compiler or runtime environment.

컴파일러 또는 실행환경의 구현체에 의해 프로그램에게 강요되는 제한이다.

The compiler may seek to surface runtime-imposed limits to the user for improved user experience.

컴파일러는 향상된 사용자 경험을 위해 런타임이 부과하는 제한사항들을 사용자에게 노출시키려 할 수 있다.

### 1.4.6 Undefined Behavior

==1==    Behavior of invalid program constructs or incorrect data for which this standard imposes no requirements, or does not sufficiently detail.

==1==    유효하지 않은 프로그램 구조나 부정확한 데이터의 동작으로, 이 표준이 요구사항을 부과하지 않거나 충분히 상세하게 기술하지 않는다.

### 1.4.7 Unspecified Behavior

==1==    Behavior of a well-formed program and correct data which may vary by the implementation, and the implementation is not expected to document the behavior.

==1==    올바른 형태의 프로그램과 정확한 데이터의 동작으로, 구현체에 따라 달라질 수 있다.  그리고 구현체는 이 동작을 문서화하지 않는다.

### 1.4.8 Well-formed Program

==1==    An HLSL program constructed according to the syntax rules, diagnosable semantic rules, and the One Definition Rule.

==1==    문법 규칙, 진단 가능한 의미 규칙 그리고 하나의 정의 규칙에 따라 구성된 HLSL 프로그램.

### 1.4.9 Runtime Implementation

==1==    A runtime implementation refers to a full-stack implementation of a software runtime that can facilitate the execution of HLSL programs.

런타임 구현체는 HLSL 프로그램의 실행을 용이하게 하는 소프트웨어 런타임의 풀스택 구현체를 가리킨다.

This broad definition includes libraries and device driver implementations.

이 광범위한 정의는 라이브러리와 장치 드라이버 구현체를 포함한다.

The HLSL specification does not distinguish between the user-facing programming interfaces and the vendor-specific backing implementation.

HLSL 명세는 사용자 대면 프로그래밍 인터페이스와 벤더별 백킹 구현체를 구분하지 않는다.

## 1.5 Runtime Targeting

==1==   HLSL emerged from the evolution of DirectX to grant greater control over GPU geometry and color processing.

HLSL은 GPU의 도형과 색상 처리에 대한 더 큰 제어권을 부여하기 위한 DirectX의 발전으로부터 등장했다.

It gained polularity because it targeted a common hardware description which all conforming drivers were required to support.

HLSL은 모든 호환 드라이버가 지원해야 하는 공통 하드웨어 사양을 대상으로 했기 때문에 인기를 얻었다.

This common hardware description, called a Shader Model, is an integral part of the description for HLSL.

쉐이더 모델이라 불리는 이 공통 하드웨어 사양은 곧 HLSL 사양의 필수적인 부분이다.

Some HLSL features require specific Shader Model features, and are only supported by compilers when targeting those Shader Model versions or later.

몇몇 HLSL 기능은 특정 쉐이더 모델의 기능을 요구하며, 해당 쉐이더 모델 버전 이상을 대상으로 할 때만 컴파일러에 의해서 지원을 받을 수 있다.

## 1.6 Single Program Multiple Data Programming Model

==1==    HLSL uses a Single Program Multiple Data (SPMD) programming model where a program describes operations on a single element of data, but when the program executes it executes across more than one element at a time.

==1==    HLSL은 단일 프로그램 다중 데이터 (SPMD) 프로그래밍 모델을 사용한다. 이 모델에서는 프로그램이 데이터 하나에 대한 연산을 기술하지만, 실제 실행될 때는 한 번에 여러 데이터 요소에 대해 수행된다.

This programming model is useful due to GPUs largely being Single Instruction Multiple Data (SIMD) hardware architectures where each instruction natively executes across multiple data elements at the same time.

이 프로그래밍 모델은 GPU가 주로 단일 명령 다중 데이터(SIMD) 하드웨어 아키텍처이기 때문에 유용하다. SIMD 구조에서는 하나의 명령이 동시에 여러 데이터 요소에 대해 본래대로 실행된다.

==2==    There are many different terms of art for describing the elements of a GPU architecture and the way they relate to the SPMD program model.

==2==    GPU 아키텍처의 구성 요소와 이들이 SPMD 프로그램 모델과 어떻게 연관되는지를 설명할 때 사용되는 전문 용어가 많이 있다.

In this document we will use the terms as defined in the following subsections.

이 문서에서는 다음 하위 절에서 정의된 용어들을 사용한다.

### 1.6.1 SPMD Terminology

#### 1.6.1.1 Host and Device

==1==    HLSL is a data-parallel programming language designed for programming auxilary processors in a larger system.

==1==    HLSL은 데이터 병렬 프로그래밍 언어이며 더 큰 시스템의 보조 연산장치를 프로그래밍하기 위해 설계되었다.

In this context the host refers to the primary processing unit that runs the application which in turn uses a runtime to execute HLSL programs on a supported device.

이러한 맥락에서 호스트는 주 연산 장치를 나타낸다. 주 연산 장치는 어플리케이션을 실행하며 그에 따라 지원되는 장치에서 HLSL 프로그램을 실행시키는 런타임을 실행한다.

There is no strict requirement that the host and device be different physical hardware, although they commonly are.

호스트와 장치가 반드시 서로 다른 물리적 하드웨어일 필요는 없지만, 일반적으로는 그렇다.

The separation of host and device in this specification is useful for defining the execution and memory model as well as specific semantics of language constructs.

이 명세서에서의 호스트와 장치의 분리는 실행 및 메모리 모델뿐만 아니라 언어 구조의 구체적인 의미를 정의하는 데에도 유용하다.

#### 1.6.1.2 Lane

==1==    A Lane represents a single computed element in an SPMD program.

==1==    
