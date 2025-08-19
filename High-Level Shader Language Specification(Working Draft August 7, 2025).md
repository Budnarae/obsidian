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

==1==    레인(Lane)은 SPMD 프로그램에서 단일 연산되는 요소를 말한다.

In a traditional programming model it would be analogous to a thread of execution, however it differs in one key way.

전통적인 프로그래밍 모델에서 스레드의 실행이 이와 유사할 수 있지만, 한 가지 중요한 점에서 다르다.

In multi-threaded programming threads advance independent of each other.

멀티 스레드 프로그래밍에서는 스레드들이 서로 독립적으로 진행한다.

In SPMD programs, a group of Lanes may execute instructions in lockstep because each instruction may be a SIMD instruction computing the results for multiple Lanes simultaneously, or synchronizing execution across multiple Lanes or Waves.

SPMD 프로그램에서는 여러 레인 그룹이 동기화되어 명령을 실행할 수 있다. 이는 각 명령이 여러 레인의 결과를 동시에 계산하는 SIMD 명령이거나, 여러 레인 또는 웨이브 간 실행을 동기화하는 명령일 수 있기 때문이다.

A Lane has an associated lane state which denotes the execution status of the lane (1.6.1.7).

하나의 레인은 연관된 레인 상태를 가지며, 이 상태는 레인의 실행 상태를 나타낸다(1.6.1.7).

#### 1.6.1.3 Wave

==1==    A grouping of Lanes for execution is called a Wave.

==1==    실행을 위해 레인을 묶은 그룹을 웨이브라고 한다.

The size of a Wave is defined as the maximum number of active Lanes the Wave supports.

웨이브의 크기는 웨이브가 지원하는 활성 레인의 최대 수로 정의된다.

Wave sizes vary by hardware architecture, and are required to be powers of two.

웨이브의 크기는 하드웨어 아키텍처에 따라 다르며, 2의 제곱수여야 한다.

The number of active Lanes in a Wave can be any value between one and the Wave size.

활성 레인의 수는 1과 웨이브의 크기 사이의 어떠한 값도 될 수 있다.

==2==    Some hardware implementations support multiple Wave sizes.

==2==    몇몇 하드웨어 구현체는 여러 웨이브 크기를 지원한다.

There is no overall minimum wave size requirement, although some language features do have minimum Lane size requirements.

전체적인 최소 웨이브 크기 요구사항은 없지만, 일부 언어 기능은 최소 레인 크기 요구사항을 가진진다.

==3==    HLSL is explicitly designed to run on hardware with arbitrary Wave sizes.

HLSL은 임의의 웨이브 크기를 가지고 하드웨어에서 실행하도록 명시적으로 설계되었다.

Hardware architectures may implement Waves as Single Instruction Multiple Thread (SIMT) where each thread executes instructions in lockstep.

하드웨어 아키텍처들은 웨이브를 단일 명령 다중 스레드 (SIMT)로 구현할 수도 있다. 이 경우 각 스레드는 동기화된 상태로 명령을 실행한다.

This is not a requirement of the model.

이것은 모델의 요구 사항이 아니다.

Some constructs in HLSL require synchronized execution.

HLSL의 일부 구성 요소는 동기화된 실행을 요구한다.

Such constructs will explicitly specify that requirement.

이러한 구성 요소는 해당 요구 사항을 명시적으로 지정한다.

#### 1.6.1.4 Quad

==1==    A Quad is a subdivision of four Lanes in a Wave which are computing adjacent values.

==1==    쿼드(Quad)는 인접한 값들을 계산하는 웨이브의 4개 레인의 하위 구분이다.

In pixel shaders a Quad may represent four adjacent pixels and Quad operations allow passing data between adjacent Lanes.

픽셀 셰이더에서 쿼드는 4개의 인접한 픽셀을 나타낼 수 있다. 쿼드 연산을 통해 인접한 레인들 간에 데이터를 전달할 수 있다.

In compute shaders quads may be one or two dimensional depending on the workload dimensionality.

컴퓨트 셰이더에서 쿼드는 작업의 차원성에 따라 1차원 또는 2차원일 수 있다.

Quad operations require four active Lanes.

쿼드 연산은 네 개의 활성 레인이 필요하다.

#### 1.6.1.5 Thread Group

==1==    A grouping of Lanes executing the same shader to produce a combined result is called a Thread Group.

결합된 결과를 생성하기 위해 동일한 셰이더를 실행하는 레인들의 그룹을 스레드 그룹이라고 한다.

Thread Groups are independent of SIMD hardware specifications.

스레드 그룹은 하드웨어의 SIMD 명세와는 독립적이다.

The dimensions of a Thread Group are defined in three dimensions.

스레드 그룹의 차원은 3차원으로 정의되어 있다.

The maximum extent along each dimension of a Thread Group, and the total size of a Thread Group are implementation limits defined by the runtime and enforced by the compiler.

스레드 그룹의 각 차원의 최대치, 그리고 스레드 그룹의 총 크기를 시행 한계(implementation limit)라 한다. 시행 한계는 런타임에 정의되며 컴파일러에 의해 강제된다.

If a Thread Group’s size is not a whole multiple of the hardware Wave size, the unused hardware Lanes are implicitly inactive.

스레드 그룹의 크기가 하드웨어 웨이브 크기의 전체 배수가 아닐 경우, 사용되지 않은 하드웨어 레인들은 암묵적으로 비활성된다.

==2==    If a Thread Group size is smaller than the Wave size , or if the Thread Group size is not an even multiple of the Wave size, the remaining Lane are inactive Lanes.

==2==    만약 스레드 그룹의 크기가 웨이브의 크기보다 작다면, 또는 스레드 그룹의 크기가 웨이브 크기의 짝수 배가 아니라면, 남는 레인은 비활성 레인이 된다.

#### 1.6.1.6 Dispatch

==1==    A grouping of Thread Groups which represents the full execution of a HLSL program and results in a completed result for all input data elements.

==1==    스레드 그룹들의 그룹은 HLSL 프로그램의 전체 실행을 나타내며 입력 데이터 요소에 대하 완료된 결과를 산출한다.

#### 1.6.1.7 Lane States

==1==    Lanes may be in four primary states: active, helper, inactive, and predicated off.

레인은 4개의 주요 상태를 가질 수 있다: 활성, 헬퍼, 비활성 그리고 predicated off.

> predicated off는 GPU/병렬 프로그래밍에서 사용되는 말로 **조건부로 비활성화된 상태, 조건문(if, while 등)에 의해 실행이 일시적으로 마스킹된 레인**을 의미한다.

==2==    An active Lane is enabled to perform computations and produce output results based on the initial launch conditions and program control flow.

활성 레인은 초기 실행 조건과 프로그램 제어 흐름을 바탕으로 계산을 수행하고 출력 결과를 생성할 수 있도록 활성화되어 있다.

==3== A helper Lane is a lane which would not be executed by the initial launch conditions except that its computations are required for adjacent pixel operations in pixel fragment shaders.

헬퍼 레인은 초기 실행 조건에서는 실행되지 않을 레인이지만, 픽셀 프래그먼트 셰이더에서 인접 픽셀 연산을 위해 그 계산이 필요한 레인이다.

A helper Lane will execute all computations but will not perform writes to buffers, and any outputs it produces are discarded.

헬퍼 레인은 모든 계산을 실행하지만 버퍼에 쓰기 작업을 수행하지 않으며, 생성하는 모든 출력은 폐기된다.

Helper lanes may be required for Lane-cooperative operations to execute correctly.

헬퍼 레인은 레인 협력 연산이 올바르게 실행되기 위해 필요할 수 있습니다.

==4==    A inactive Lane is a lane that is not executed by the initial launch conditions.

비활성 레인은 초기 실행 조건에 따라 실행되지 않는 레인이다.

This can occur if there are insufficient inputs to fill all Lanes in the Wave, or to reduce per-thread memory requirements or register pressure.

비활성 레인은 입력이 충분치 못해 웨이브의 모든 레인을 채우지 못하거나, 각 스레드의 메모리 요구량이나 레지스터 부하를 감소시키기 위해 생길 수 있다.

==5==    A predicated off Lane is a lane that is not being executed due to program control flow.

predicated off 레인은 프로그램 제어 흐름에 의해 실행되지 않는 레인이다.

A Lane may be predicated off when control flow for the Lanes in a Wave diverge and one or more lanes are temporarily not executing.

웨이브 내 레인들의 제어 흐름이 분기되어 하나 이상의 레인이 일시적으로 실행되지 않을 때 레인이 프레디케이트 오프될 수 있다.

==6==    The diagram blow illustrates the state transitions between Lane states:

아래의 다이어그램은 레인 상태 간의 상태 전환을 시각화한 것이다.

![[357f8be712c1ea04a541a6b3c523895e_MD5.jpeg]]

### 1.6.2 SPMD Execution Model

==1==    A runtime implementation shall provide an implementation-defined mechanism for defining a Dispatch.

==1==    런타임 구현체는 디스패치를 정의하기 위한 구현체가 정의한 메커니즘을 제공해야 한다.

A runtime shall manage hardware resources and schedule execution to conform to the behaviors defined in this specification in an implementation-defined way.

런타임은 구현체가 정의한 방식으로 하드웨어 리소스를 관리하고 실행을 스케줄링하여 이 명세서에서 정의한 동작들을 준수해야 한다.

A runtime implementation may sort the Thread Groups of a Dispatch into Waves in an implementation-defined way.

런타임 구현체는 구현체가 정의한 방식으로 디스패치의 스레드 그룹들을 웨이브로 정렬할 수 있다.

During execution no guarantees are made that all Lanes in a Wave are actively executing.

실행 동안 웨이브의 모든 레인이 활성되어 실행된다는 보장은 없다.

==2==    Wave, Quad, and Thread Group operations require execution synchronization of applicable active and helper Lanes as defined by the individual operation.

웨이브, 쿼드, 그리고 스레드 그룹 연산들은 개별 연산에서 정의한 대로 해당하는 활성 및 헬퍼 레인들의 실행 동기화를 필요로 한다.

### 1.6.3 Optimization Restrictions

==1==    An optimizing compiler may not optimize code generation such that it changes the behavior of a well-formed program except in the presence of implementation-defined or unspecified behavior.

최적화 컴파일러는 구현체가 정의한 동작이나 명시되지 않은 동작이 존재하는 경우를 제외하고는 올바른 형태의 프로그램의 동작을 변경하는 방식으로 코드 생성을 최적화해서는 안된다.

==2==    The presence of Wave, Quad, or Thread Group operations may further limit the valid transformations of a program.

웨이브, 쿼드, 또는 스레드 그룹 연산들의 존재는 프로그램의 유효한 변환을 더욱 제한할 수 있다.

Specifically, control flow operations which result in changing which Lanes, Quads, or Waves are actively executing are illegal in the presence of cooperative operations if the optimization alters the behavior of the program.

구체적으로, 어떤 레인, 쿼드, 또는 웨이브가 활성적으로 실행되고 있는지를 변경시키는 제어 흐름 연산들은, 최적화가 프로그램의 동작을 변경시키는 경우 협력적 연산들이 존재할 때 불법이다.

### 1.7 HLSL Memory Models

==1==    Memory accesses for Shader Model 5.0 and earlier operate on 128-bit slots aligned on 128-bit boundaries.

셰이더 모델 5.0 이하에서 메모리 액세스는 128비트 경계에 정렬된 128비트 슬롯에서 동작한다.

This optimized for the common case in early shaders where data being processed on the GPU was usually 4-element vectors of 32-bit data types.

이는 GPU에서 처리되는 데이터가 일반적으로 32비트 데이터 타입의 4개 요소 벡터였던 초기 셰이더의 일반적인 경우에 최적화된 것이다.

==2==    On modern hardware memory access restrictions are loosened, and reads of 32-bit multiples are supported starting with Shader Model 5.1 and reads of 16-bit multiples are supported with Shader Model 6.0.

==2==    현대 하드웨어에서는 메모리 액세스 제한이 완화되어, 32비트 배수 읽기는 셰이더 모델 5.1부터 지원되고 16비트 배수 읽기는 셰이더 모델 6.0부터 지원된다.

Shader Model features are fully documented in the DirectX Specifications, and this document will not attempt to elaborate further.

셰이더 모델 기능들은 DirectX 명세서에 완전히 문서화되어 있으며, 이 문서에서는 더 자세히 설명하지 않을 것이다.

### 1.7.1 Memory Spaces

==1==    HLSL programs manipulate data stored in four distinct memory spaces: thread, threadgroup, device and constant.

HLSL 프로그램들은 4개의 구분된 메모리 공간: 스레드, 스레드 그룹, 장치(device)와 상수에 저장된 메모리를 다룬다.

#### 1.7.1.1 Thread Memory

==1==    Thread memory is local to the Lane.

==1==    스레드 메모리는 레인에 지역적이다.

It is the default memory space used to store local variables.

스레드 메모리는 지역 변수를 저장하기 위해 사용하는 디폴트 메모리 공간이다.

Thread memory cannot be directly read from other threads without the use of intrinsics to synchronize execution and memory.

스레드 메모리는 실행과 메모리를 동기화하는 내장 함수를 사용하지 않고는 다른 스레드에서 직접 읽을 수 없다.

#### 1.7.1.2 Thread Group Memory

==1==     Thread Group memory is denoted in HLSL with the groupshared keyword.

스레드 그룹 메모리는 HLSL에서 groupshared 키워드로 표시된다.

The underlying memory for any declaration annotated with groupshared is shared across an entire Thread Group.

groupshared로 주석이 달린 모든 선언의 기저 메모리는 전체 스레드 그룹에 걸쳐 공유된다.

Reads and writes to Thread Group Memory, may occur in any order except as restricted by synchronization intrinsics or other memory annotations.

스레드 그룹 메모리에 대한 읽기와 쓰기는 동기화 내장 함수나 다른 메모리 주석에 의해 제한되는 경우를 제외하고는 임의의 순서로 발생할 수 있다.

#### 1.7.1.3 Device Memory

==1==    Device memory is memory available to all Lanes executing on the device.

==1==    장치 메모리는 장치 위해서 실행하는 모든 레인에 의해 사용될 수 있는 메모리이다.

This memory may be read or written to by multiple Thread Groups that are executing concurrently.

이 메모리는 비동기적으로 실행하는 여러 개의 스레드 그룹들에 의해 읽히거나 쓰일 수 있다.

Reads and writes to device memory may occur in any order except as restricted by synchronization intrinsics or other memory annotations.

장치 메모리에 대한 읽기 또는 쓰기는 동기화 내장 함수나 다른 메모리 주석에 의해 제한되는 경우를 말고는 임의의 순서로 발생할 수 있다.

Some device memory may be visible to the host.

일부 장치 메모리는 호스트에서 볼 수 있다.

Device memory that is visible to the host may have additional synchronization concerns for host visibility.

호스트에서 볼 수 있는 장치 메모리는 호스트 가시성을 위한 추가적인 동기화 고려사항을 가질 수 있다.

#### 1.7.1.4 Constant Memory

==1==    Constant memory is similar to device memory in that it is available to all Lanes executing on the device.

==1==    상수 메모리는 장치에서 실행하는 모든 레인에 의해 사용될 수 있다는 점에서 장치 메모리와 유사하다.

Constant memory is read-only, and an implementation can assume that constant memory is immutable and cannot change during execution.

상수 메모리는 읽기 전용이다. 구현체는 상수 메모리가 불변이고 실행 중에 변경될 수 없다고 가정할 수 있다.

### 1.7.2 Memory Spaces

_TODO_

==1==    The alignment requirements of an offset into device memory space is the size in bytes of the largest scalar type contained in the given aggregate type.

장치 메모리 공간으로의 오프셋 정렬 요구사항은 주어진 집합 타입에 포함된 가장 큰 스칼라 타입의 바이트 단위 크기입니다.

# Lexical Conventions

## 2.1 Unit of Translation

==1==    The text of HLSL programs is collected in source and header files.

HLSL 프로그램의 텍스트는 소스 파일과 헤더 파일에서 수집된다.

The distinction between source and header files is social and not technical.

소스의 헤더 파일의 구분은 사회적인 것이지 기술적인 것이 아니다.

An implementation will construct a translation unit from a single source file and any included source or header files referenced via the #include preprocessing directive conforming to the ISO C standard (2011) preprocessor specification.

구현체는 단일 소스 파일과 ISO C 표준(2011) 전처리기 명세를 준수하는 #include 전처리 지시어를 통해 참조되는 포함된 소스 또는 헤더 파일들로부터 번역 단위를 구성할 것이다.

==2==    An implementation may implicitly include additional sources as required to expose the HLSL library functionality as defined in (13).

==2==    구현체는 (13)에서 정의한 HLSL 라이브러리 기능을 노출하기 위해 암시적으로 추가적인 소스를 추가할 수 있다.

## 2.2 Phases of Translation

==1==    HLSL inherits the phases of translation from ISO C++ standard (2011), with minor alterations, specifically the removal of support for trigraph and digraph sequences.

==1==    HLSL은 트라이그래프와 다이그래프 시퀀스 지원 제거라는 사소한 변경을 제외하고는 ISO C++ 표준(2011)의 번역 과정을 상속한다.

Below is a description of the phases.

아래는 단계들에 대한 설명이다.

1. Source files are characters that are mapped to the basic source character set in an implementation-defined manner.

소스 파일은 구현체가 정의한 방식으로 기본 소스 문자 집합에 매핑되는 문자들이다.

2. Any sequence of backslash (\) immediately followed by a new line is deleted, resulting in splicing lines together.

백슬래시(\\) 바로 뒤에 새 줄이 오는 모든 시퀀스는 삭제되어, 줄들이 연결된다.

3. Tokenization occurs and comments are isolated. If a source file ends in a partial comment or preprocessor token the program is ill-formed and a diagnostic shall be issued. Each comment block shall be treated as a single white-space character.

토큰화가 발생하고 주석들이 분리된다. 소스 파일이 부분 주석이나 전처리기 토큰으로 끝나면 프로그램은 올바르지 않은 형태이며 진단 메시지가 발행되어야 한다. 각 주석 블록은 단일 공백 문자로 취급되어야 합니다.

4. Preprocessing directives are executed, macros are expanded, pragma and other unary operator expressions are executed. Processing of #include directives results in all preceding steps being executed on the resolved file, and can continue recursively. Finally all preprocessing directives are removed from the source.

전처리 지시어가 실행되고, 매크로가 확장되며, pragma 및 기타 단항 연산자 표현식들이 실행된다. #include 지시어 처리는 해결된 파일에서 모든 이전 단계들이 실행되는 결과를 가져오며, 재귀적으로 계속될 수 있다. 마지막으로 모든 전처리 지시어가 소스에서 제거된다.

5. Character and string literal specifiers are converted into the appropriate character set for the execution environment.

문자 및 문자열 리터럴 지정자들이 실행 환경에 적합한 문자 집합으로 변환된다.

6. Adjacent string literal tokens are concatenated.

인접한 문자열 리터럴 토큰들이 연결된다.

7. White-space is no longer significant. Syntactic and semantic analysis occurs translating the whole translation unit into an implementation-defined representation.

공백은 의미를 상실한다. 구문 및 의미 분석이 발생하여 전체 번역 단위를 구현체가 정의한 표현으로 번역한다.

8. The translation unit is processed to determine required instantiations, the definitions of the required instantiations are located, and the translation and instantiation units are merged. The program is ill-formed if any required instantiation cannot be located or fails during instantiation.

번역 단위가 처리되어 필요한 인스턴스화를 결정하고, 필요한 인스턴스화의 정의가 찾아지며, 번역 및 인스턴스화 단위들이 병합된다. 필요한 인스턴스화를 찾을 수 없거나 인스턴스화 중에 실패하면 프로그램은 올바르지 않은 형태이다.

9. External references are resolved, library references linked, and all translation output is collected into a single output.

외부 참조가 해결되고, 라이브러리 참조가 링크되며, 모든 번역 출력이 단일 출력으로 수집된다.

## 2.3 Character Sets

==1==    The basic source character set is a subset of the ASCII character set.

==1==    기본 소스 문자 집합은 아스키 문자 집합의 부분 집합이다.

The table below lists the valid characters and their ASCII values:

아래의 표는 유효한 문자들과 그 문자들의 아스키 값들의 목록이다.

![[150b48146db85007835fe110b37c0a6a_MD5.jpeg]]

==2==    An implementation may allow source files to be written in alternate extended character sets as long as that set is a superset of the basic character set.

구현체는 소스 파일이 기본 문자 집합의 상위 집합인 한 대안적인 확장 문자 집합으로 작성되는 것을 허용할 수 있다.

The translation character set is an extended character set or the basic character set as chosen by the implementation.

번역 문자 집합은 구현체가 선택한 확장 문자 집합 또는 기본 문자 집합이다.

## 2.4 Preprocessing Tokens

```text

preprocessing-token:
	header-name
	identifier
	pp-number
	character-literal
	string-literal
	preprocessing-op-or-punc
	each non-whitespace character from the translation character set that cannot be one of the above

```

The preprocessor is inherited from C++ 11 with no grammar extensions.

전처리기는 문법의 확장 없이 C++ 11로부터 계승되었다.

It is specified here only for completeness.

관련한 내용은 오로지 문서의 완전성만을 위하여 수록되었다.

==1==    Each preprocessing token that is converted to a token shall have the lexical form of a keyword, an identifier, a constant, a string literal or an operator or punctuator.

==1==    토큰으로 변환되는 각 전처리 토큰은 키워드, 식별자, 상수, 문자열 리터럴 또는 연산자나 구두점의 어휘적 형태를 가져야 한다.

==2==    Preprocessing tokens are the minimal lexical elements of the language during translation phases 3 through 6 (2.2).

==2==    전처리 토큰은 번역 단계 3부터 6까지(2.2) 동안 언어의 최소 어휘 요소이다.

Preprocessing tokens can be separated by whitespace in the form of comments, white space characters, or both.

전처리 토큰은 주석, 공백 문자 또는 둘 다의 형태로 공백에 의해 분리될 수 있습니다.

White space may appear within a preprocessing token only as part of a header name or between the quotation characters in a character constant or string literal.

공백은 헤더 이름의 일부로서 또는 문자 상수나 문자열 리터럴의 따옴표 문자들 사이에서만 전처리 토큰 내에 나타날 수 있다.

==3==    Header name preprocessing tokens are only recognized within \#include preprocessing directives, has include expressions, and implementation-defined locations within \#pragma directives.

헤더 이름 전처리 토큰은 \#include 전처리 지시어, has include 표현식, 그리고 \#pragma 지시어 내의 구현체가 정의한 위치들 내에서만 인식됩니다.

In those contexts, a sequence of characters that could be either a header name or a string literal is recognized as a header name.

이러한 맥락에서, 헤더 이름 또는 문자열 리터럴 중 하나가 될 수 있는 문자 시퀀스는 헤더 이름으로 인식됩니다.

## 2.5 Tokens

```text

token:
	identifier
	keyword
	literal
	operator-or-punctuator

```

==1==    There are five kinds of tokens: identifiers, keywords, literals, and operators or punctuators.

==1==    토큰에는 다섯 종류가 있습니다: 식별자, 키워드, 리터럴, 그리고 연산자나 구두점이다.

All whitespace characters and comments are ignored except as they separate tokens.

모든 공백 문자와 주석은 토큰을 분리하는 역할을 제외하고는 무시됩니다.

## 2.6 Comments

==1==    The characters /\* start a comment which terminates with the characters \*/. The characters // start a comment which terminates at the next new line.

/\* 문자들은 \*/ 문자들로 종료되는 주석을 시작한다. // 문자들은 다음 새 줄에서 종료되는 주석을 시작한다.

## 2.7 Header Names

```text

header-name:
    < h-char-sequence >
    " q-char-sequence "

h-char-sequence:
    h-char
    h-char-sequence h-char

h-char:
    개행 또는 > 를 제외한 번역 문자 집합의 모든 문자

q-char-sequence:
    q-char
    q-char-sequence q-char

q-char:
    개행 또는 " 를 제외한 번역 문자 집합의 모든 문자
    
```

==1==    헤더 이름의 문자 시퀀스는 구현체가 정의한 방식으로 헤더 파일이나 외부 소스 파일 이름에 매핑됩니다.

## 2.8 Preprocessing numbers

```text

pp-number:
    Working Draft
    Literals
    digit
    . digit
    pp-number ' digit
    pp-number ' non-digit
    pp-number e sign
    pp-number E sign
    pp-number p sign
    pp-number P sign
    pp-number .

```

==1==    전처리 숫자는 숫자나 마침표(.)로 시작하며, 유효한 식별자 문자들과 부동소수점 리터럴 접미사들(e+, e-, E+, E-, p+, p-, P+, P-)이 뒤따를 수 있습니다. 전처리 숫자 토큰은 모든 정수 리터럴 및 부동소수점 리터럴 토큰을 어휘적으로 포함합니다.

==2==    전처리 숫자는 타입이나 값을 가지지 않습니다. 타입과 값은 전처리 숫자로부터 성공적으로 변환될 때 정수 리터럴, 부동소수점 리터럴, 벡터 리터럴 토큰에 할당됩니다.

==3==    바로 다음 토큰이 scalar-element-sequence (2.9.4)인 경우, 전처리 숫자는 마침표(.)로 끝날 수 없습니다. 이 상황에서 pp-number 토큰은 마침표 이전에서 끝나도록 잘립니다.²

## 2.9 Literals

### 2.9.1 Literal Classifications

```text

literal:
    integer-literal
    character-literal
    floating-literal
    string-literal
    boolean-literal
    vector-literal

```

### 2.9.2 Integer Literals

```text

integer-literal:
    decimal-literal integer-suffixopt
    octal-literal integer-suffixopt
    hexadecimal-literal integer-suffixopt

decimal-literal:
    nonzero-digit
    decimal-literal digit

octal-literal: 
    0
    octal-literal octal-digit

hexadecimal-literal:
    0x hexadecimal-digit
    0X hexadecimal-digit
    hexadecimal-literal hexadecimal-digit

nonzero-digit: 다음 중 하나
    1 2 3 4 5 6 7 8 9

```

²이 문법 공식화는 문맥 자유 문법이 아니며 LL(2) 파서를 필요로 합니다.

```text

octal-digit: 다음 중 하나
    0 1 2 3 4 5 6 7

hexadecimal-digit: 다음 중 하나
    0 1 2 3 4 5 6 7 8 9
    a b c d e f
    A B C D E F

integer-suffix:
    unsigned-suffix long-suffixopt
    long-suffix unsigned-suffixopt

unsigned-suffix: 다음 중 하나
    u U

long-suffix: 다음 중 하나
    l L

```

==1==    정수 리터럴은 선택적 기수 접두사, 적절한 기수의 숫자 시퀀스, 그리고 선택적 타입 접미사입니다. 정수 리터럴은 마침표나 지수 지정자를 포함해서는 안 됩니다.

==2==    정수 리터럴의 타입은 아래 표에서 해당하는 목록 중 그 값이 표현될 수 있는 첫 번째 타입입니다.³

|접미사|10진 상수|8진 또는 16진 상수|
|---|---|---|
|없음|int32_t<br/>int64_t|int32_t<br/>uint32_t<br/>int64_t<br/>uint64_t|
|u 또는 U|uint32_t<br/>uint64_t|uint32_t<br/>uint64_t|
|l 또는 L|int64_t<br/>uint64_t|int64_t<br/>uint64_t|
|u 또는 U와<br/>l 또는 L 둘 다|uint64_t|uint64_t|

==3==    정수 리터럴의 지정된 값이 해당 목록의 어떤 타입으로도 표현될 수 없는 경우, 정수 리터럴은 타입을 가지지 않으며 프로그램은 올바르지 않은 형태입니다.

==4==    구현체는 정수 접미사 ll과 ull을 각각 l과 ul과 동등한 것으로 지원할 수 있습니다.

### 2.9.3 Floating-point Literals

```text

floating-literal:
    fractional-constant exponent-partopt floating-suffixopt
    digit-sequence exponent-part floating-suffixopt

fractional-constant:
    digit-sequenceopt . digit-sequence
    digit-sequence .

exponent-part:
    e signopt digit-sequence
    E signopt digit-sequence

sign: 다음 중 하나
    + -

digit-sequence:
    digit

```

³이 동작은 ISO C 표준(2011)과 일치하지만 HLSL이 더 적은 데이터 타입을 가지고 있기 때문에 범위가 축소됩니다.

```text

digit-sequence digit 

floating-suffix: 다음 중 하나
    h f l H F L

```

==1==    부동소수점 리터럴은 선택적 지수부와 선택적 부동소수점 접미사를 가진 분수 상수로 작성되거나, 필수 지수부와 선택적 부동소수점 접미사를 가진 정수 숫자 시퀀스로 작성됩니다.

==2==    부동소수점 리터럴의 타입은 접미사에 의해 명시적으로 지정되지 않는 한 float입니다. 접미사 h와 H는 half를 지정하고, 접미사 f와 F는 float를 지정하며, 접미사 l과 L은 double을 지정합니다.⁴ 소스에서 지정된 값이 해당 타입의 표현 가능한 값 범위에 있지 않으면, 프로그램은 올바르지 않은 형태입니다.

### 2.9.4 Vector Literals

```text

vector-literal:
    integer-literal . scalar-element-sequence
    floating-literal . scalar-element-sequence

scalar-element-sequence:
    scalar-element-sequence-x
    scalar-element-sequence-r

scalar-element-sequence-x:
    x
    scalar-element-sequence-x x

scalar-element-sequence-r:
    r
    scalar-element-sequence-r r

```

==1==    벡터 리터럴은 정수 리터럴 또는 부동소수점 리터럴 뒤에 마침표(.)와 scalar-element-sequence가 따라오는 것입니다.

==2==    scalar-element-sequence는 첫 번째 벡터 요소 접근자(x 또는 r)만 유효한 vector-swizzle-sequence입니다. scalar-element-sequence는 정수 리터럴 또는 부동소수점 리터럴 값에 대해 수행되는 벡터 확산 변환과 동등합니다(4.10).

---

⁴이는 FXC와 DXC의 구현체와는 상당히 다르지만, 공식 문서 및 GLSL의 동작과 일치합니다. 또한 기존 동작들보다 구현하기 훨씬 간단하고 더 규칙적입니다.

# Basic Concecp
