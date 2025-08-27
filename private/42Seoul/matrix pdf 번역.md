---
tags:
  - 42_outer_subject
---
---

# Enter the Matrix

매트릭스로의 진입

**An introduction to Linear Algebra**

선형대수개론

_Summary: Vectors and matrices, basically_

_요약: 간단히 말해서, 벡터와 행렬에 대해 배웁니다_

## General Rules

For this module, function prototypes are described in Rust, but you may use the language you want.

이 모듈에서, 함수 프로토타입은 Rust로 작성되었지만, 당신 원하는 언어를 사용해도 괜찮습니다.

There are a few constraints for your language of choice, though:

하지만, 언어를 선택하는 데에는 몇 가지 제약이 있습니다:

It must support generic types

언어는 반드시 제네릭 타입을 지원해야 합니다.

It must support functions as first class citizens (example: supports lambda expressions)

언어는 반드시 함수를 일급 시민 클래스로서 지원해야 합니다(예: 람다 함수 지원).

Optional: support for operator overloading 

선택사항: 연산자 오버로딩을 지원하면 좋습니다.

We recommend that you use paper if you need to.

우리는 당신에게 필요한 경우에 종이를 사용하기를 권합니다.

Drawing visual models, making notes of technical vocabulary...

시각적인 모델을 그린다거나, 기술적인 용어를 필기하는 경우 등이 있겠군요.

This way, it will be easier to wrap your head around the new concepts you will discover, and use them to build your understanding for more and more related concepts.

그러한 방식을 통해서, 당신의 두뇌를 당신이 발견한 새로운 개념으로 감싸고, 그것들을 사용해 관련된 개념들을 습득하는 과정이 더 용이해질 것입니다.

Also, doing computations by head is really hard and error-prone, so having all the steps written down helps you figure out where you made a mistake when you did.

또한, 암산이라는 행위는 실수가 생기기 쉬우므로, 계산 과정을 모두 손으로 써야 실수했을 때 그것이 어디서 발생했는지 찾기 쉬울 것입니다.

Don’t stay stuck because you don’t know how to solve an exercise:

문제를 해결하는 방법을 모른다해서 멈춰서지 마세요.

make use of peer-learning!

동료 학습을 하세요!

You can ask for help on Slack (42 or 42-AI) or Discord (42-AI) for example.

당신은 예를 들어 Slack, Discord에 질문을 할 수 있습니다.

You are not allowed to use any mathematical library, even the one included in your language’s standard library, unless explicitly stated otherwise.

특별히 명시되지 않는 한, 당신은 수학과 관련된 라이브러리를 사용할 수 없습니다. 심지어 그게 언어의 표준 라이브러리라 해도요.

For every exercise you may have to respect a given time and/or space complexity.

모든 과제에서 당신은 주어진 시간과 공간복잡도를 준수해야 합니다.

These will be checked during peer review.

동료 평가 동안 이러한 사항을 확인받을 것입니다.

The time complexity is calculated relative to the number of executed instructions. 

시간 복잡도는 실행된 명령어의 수를 기준으로 계산됩니다.

The space complexity is calculated relative to the maximum amount of memory allocated simultaneously.

공간 복잡도는 이론적으로 메모리의 할당되는 공간의 최대값을 기준으로 계산됩니다.

Both have to be calculated against the size of the function’s input (a number, the length of a string, etc...).

둘 다 함수의 입력 크기(숫자, 문자열의 길이 등등)을 기준으로 계산되어야 합니다.

## Introduction

For this module, we highly recommend the series of videos Essence of linear algrebra by 3blue1brown, which provides a very good, comprehensive and visual explaination of this topic.

이 모듈에서, 우리는 **3blue1brown**의 '선형대수학의 정수' 시리즈를 보기를 강력히 추천합니다. 이 영상들은 매우 우수한, 완벽한, 시각적인 설명들을 제공하기 때문이죠.

These videos are so good, you will probably want to watch them once before working on this module, you will be going back to specific parts of them during the module, and you will want to rewatch them once again after this module, perhaps a couple of months after.

이 비디오들은 너무 우수해서, 당신은 이 모듈을 진행하는 동안 그것들을 정주행하고, 몇몇 부분은 되돌아가 다시 보고, 그걸로도 모자라 이 모듈을 마친지 몇개월 뒤에 다시 정주행할지도 모릅니다.

We’re not kidding.

농담이 아닙니다.

Many people to whom we had recommended these videos before getting into game physics programming, data science or computer graphics decided not to watch them until much later.

우리가 이 영상들을 추천했던 많은 사람들(게임 물리, 데이터 과학, 컴퓨터 그래픽스 종사자들)이 정주행하는 데는 오랜 시간이 걸리지 않았습니다.

The reaction was UNANIMOUS: those who had watched the videos had nothing but praise about how incredibly helpful they had been; those who had only watched the videos later in their learning of linear algebra deeply regretted the time that they wouldn’t have wasted, had they watched the videos from the start.

반응은 만장일치였습니다: 그들 모두 이 영상들이 매우 유용하며, 선형대수를 공부하기 시작할 때부터 이 영상을 보지 않은 사람들은 이 영상을 처음부터 봤더라면 시간을 낭비하지 않았을 것이라며 후회했습니다.

Don’t waste your time.

시간을 낭비하지 마세요.

WATCH. THE. VIDEOS.

영상들을 보세요.(제발)

Even if you don’t understand everything at first, the ordered presentation and the geometric visuals will provide you with a good amount of contextual background and mental models that will prove essential as you learn the various aspects of linear algebra.

만약 당신이 첫 시도에 모든 것을 이해하지 못하더라도, 잘 정리된 설명과 기하학적 시각 자료는 당신에게 맥락을 파악할 수 있는 배경을 제공할 것이며 당신이 선형대수의 여러 부분을 학습할 때 본질을 이해할 수 있는 힘을 줄 것입니다.

## Graphical Processing Units

그래픽 처리 장치

A Graphical Processing Unit (GPU) is a piece of hardware present in a lot of modern computers, and supercomputers, which allows to perform parallel computations.

그래픽 처리 장치(GPU)는 최신 컴퓨터 중 다수, 그리고 슈퍼 컴퓨터에 존재하는 병렬 연산 기능을 가진 하드웨어 장치입니다.

The processing architecture of a GPU is referred to as SIMD (for "Single Instruction, Multiple Data"): what this means is that a GPU works well when it can run the same code (ie, functions without divergent conditional forks or gotos), at the same time, over different input values of the same type (typically, floating point numbers).

GPU의 처리 구조는 SIMD(Single Instruction, Multiple Data)라고 불립니다. 이는 GPU가 동일한 코드(즉, 분기 또는 goto 문이 없는 함수)를 동시에 다양한 유형의 동일한 입력 값(일반적으로 부동 소수점 숫자)에 대해 실행할 때 잘 작동한다는 의미입니다.

You can see this as a factory where a sequence of the same machines do the same manipulation on objects, at the same time, on multiple parallel treadmills.

이는 마치 동일한 기계들이 일련의 작업을 동시에 여러 개의 평행한 트레드밀 위에서 객체에 수행하는 공장과 같습니다.

As stated by the name, GPUs were originally targeted towards graphical computations, which rely heavily on running linear algebra operations.

이름에서 알 수 있듯이 GPU는 원래 그래픽 연산을 위해 설계되었는데, 이는 선형대수 연산에 크게 의존합니다.

Because of the ubiquity of linear algebra in mathematics, the use of GPUs was extended to more than video games and CGI, and most supercomputing today relies on GPU computation.

선형대수는 광범위하게 쓰이기 때문에 GPU의 사용은 비디오 게임과 CGI를 넘어 확장되었고, 현재 대부분의 슈퍼컴퓨팅은 GPU 연산을 기반으로 합니다.

Many modern CPUs have also taken inspiration from the SIMD model of computation, and allow for specific SIMD operations.

많은 현대의 CPU들은 SIMD 연산 모델에 영감을 받아 특정 SIMD 연산을 지원합니다.

The operations of linear algebra consist mostly of: summing vectors (a coordinate-wise addition of two vectors), scaling vectors (multiplying all coordinates of a given vector by the same real or complex number), and matrix multiplications.

선형대수 연산은 주로 벡터 덧셈(두 벡터의 좌표별 덧셈), 벡터 스케일링(주어진 벡터의 모든 좌표에 동일한 실수 또는 복소수를 곱하기), 그리고 행렬 곱셈으로 구성됩니다.

Matrix multiplications are just a repeated succession of an operation called the dot product (or inner product) of two vectors.

행렬 곱셈은 단순히 두 벡터의 내적(또는 점곱) 연산을 반복적으로 수행하는 것입니다.

All of these operations are very well adapted to SIMD, since they are just a succession of additions or multiplications over arrays of data (which represent our vectors).

이러한 모든 연산은 SIMD에 매우 적합합니다. 왜냐하면 벡터를 나타내는 데이터 배열에 대한 덧셈 또는 곱셈의 연속적인 과정이기 때문입니다.

Coding these various operations to understand them is a fundamental exercise.

이러한 다양한 연산을 이해하기 위해 코딩하는 것은 기본적인 연습입니다.

For this reason, you will get to code them all during this module.

그러므로, 이 모듈에서 이를 모두 코딩하게 될 것입니다.

## Fused Multiply-Accumulate

## 융합 곱셈-누적 연산

Under the x86 architecture, there exist the instructions called: vfmadd132ps, vfmadd213ps and vfmadd231ps (welcome to x86 :D), which allow us to compute what’s called the Fused Multiply-Accumulate operation.

x86 아키텍처에서는 vfmadd132ps, vfmadd213ps 및 vfmadd231ps와 같은 명령어가 존재하며, 이를 통해 융합 곱셈-누적 (Fused Multiply-Accumulate) 연산을 수행할 수 있습니다.

Check what these instructions do, and you will realize that they might become useful. ;)

이 명령어들이 무엇을 하는지 확인해 보시면 유용하게 활용될 수 있다는 것을 알게 될 것입니다. ;)

The standard library of the C language (as well as that of many other languages) has a function to perform this operation (but we’re not telling you which one, so search by yourself!).

C 표준 라이브러리(그리고 다른 많은 언어의 라이브러리)에도 이 연산을 수행하는 함수가 존재합니다 (하지만 어떤 함수인지 알려드리지 않겠습니다. 직접 찾아보세요!).

>**융합 곱셈-누적 (Fused Multiply-Accumulate, FMA)의 다양한 의미:**
>
>- **컴퓨팅 기술:** 두 숫자를 곱하고 그 결과를 다른 숫자(누산기)에 더하는 연산을 하나의 단계로 수행하는 방식.
>- **성능 향상:** 부동 소수점 연산의 정확도와 속도를 동시에 개선할 수 있음.
>- **하드웨어 지원:** 최신 CPU 및 GPU에서 FMA 명령어를 통해 구현됨.

## Vector space

벡터 공간

The following, which is a concise-but-terse list of theoretical info about vector spaces, can probably be useful for you to visit and revisit as you work on this module.

다음은 벡터 공간에 대한 간결하지만 딱딱한 이론 정보 목록이며, 이 모듈 작업을 진행하면서 방문하고 다시 방문하는 데 유용할 수 있습니다.

It helps to work both practical applications and theory together, in order to gradually build up a deeper understanding.

실질적인 응용과 이론을 함께 작업하여 점진적으로 더 깊이 있는 이해를 구축하는 것이 도움이 됩니다.

Don’t feel discouraged if you don’t understand everything immediately: that is obviously normal when approaching a new ecosystem of information.

즉시 모든 것을 이해하지 못하더라도 낙담하지 마세요. 새로운 정보 생태계에 접근할 때는 당연한 일입니다.


If you remember the concept of "(algebraic) groups" from the Boolean Algebra module, this section will be a lot easier to understand (if you haven’t done that module yet, we recommend you to do it, since sets, logic and algebraic structures are even more fundamental than linear algebra).

부울 대수 모듈에서 “(대수적) 그룹” 개념을 기억한다면 이 섹션을 훨씬 쉽게 이해할 수 있습니다 (아직 해당 모듈을 수행하지 않았다면 집합, 논리 및 대수 구조가 선형대수보다 더 근본적이므로 수행하는 것이 좋습니다).

Understanding things from the point of view of algebraic structures can seem difficult at first, since there is a lot of vocabulary.

대수적 구조의 관점에서 보는 것은 처음에는 어려울 수 있지만, 어휘가 많기 때문입니다.

However, this vocabulary is incredibly useful, because it transforms the mathematical properties of various sets into something simple, like knowing the rules of a card game.

그러나 이 어휘는 매우 유용합니다. 왜냐하면 다양한 집합의 수학적 속성을 간단한 규칙(카드 게임 규칙과 유사)으로 변환하기 때문입니다.

What you’re allowed to do, and what is forbidden.

무엇을 할 수 있고 무엇을 금지할 수 있는지 말이죠.

If you can remember 4-5 board games’ or card games’ rules, you definitely have what it takes to learn the language of algebraic structures (often called "abstract algebra", which is a misleadingly scary name).

4~5개의 보드 게임 또는 카드 게임 규칙을 기억할 수 있다면 대수적 구조의 언어("추상대수"라고 잘못 불리는 이름)를 배우는 데 필요한 자질이 충분합니다.

Actually, it’s really not that complicated to learn, because it’s basically ONLY a question of learning vocabulary, and not learning complex algorithmic methods.

실제로 배우기가 그다지 복잡하지 않습니다. 왜냐하면 알고리즘적인 방법을 배우는 것이 아니라 어휘를 배우는 것뿐이기 때문입니다.

For this reason, we thought it was worthwhile to include the following: what follows is the definition of a vector space, the principal type of structure that is studied in linear algebra, from the point of view of "algebraic structures" (ie, the rules that can be used over a certain set, in order to make that set become a "vector space").

이러한 이유로 우리는 다음을 포함하는 것이 가치가 있다고 생각했습니다. 다음은 벡터 공간의 정의입니다. 선형대수에서 연구되는 주된 유형의 구조이며, “대수적 구조”의 관점(즉, 특정 집합에 적용하여 해당 집합을 "벡터 공간"으로 만들 수 있는 규칙)에서 설명합니다.

A vector space V is a structure which associates:

벡터 공간 V는 다음과 같은 구조와 연결됩니다.

A field K (roughly put: an algebraic structure where you can add, subtract, multiply and divide elements under the rules of usual arithmetic).

필드 K (간단히 말해서: 통상적인 산술 규칙에 따라 요소를 더하고 빼고 곱하고 나눌 수 있는 대수적 구조).

The elements of K are called "scalars".

K의 요소는 "스칼라"라고 불립니다.

K is generally chosen to be the real numbers or the complex numbers.

K는 일반적으로 실수 또는 복소수로 선택됩니다.

Real numbers are generally represented as floats; complex numbers as pairs of floats, with a special multiplication and division.

실수는 일반적으로 부동 소수점으로 표현되고 복소수는 특수한 곱셈과 나눗셈을 가진 부동 소수점 쌍으로 표현됩니다.

We generally denote scalars with Greek letters.

우리는 일반적으로 스칼라를 그리스 문자로 나타냅니다.

A commutative group V (roughly put: an algebraic structure where you can add and subtract elements, under the rules of usual arithmetic; but not necessarily multiply them or divide them).

가환군 V (간단히 말해서: 통상적인 산술 규칙에 따라 요소를 더하고 뺄 수 있는 대수적 구조이지만 반드시 곱하거나 나눌 필요는 없습니다).

The elements of V are called "vectors".

V의 요소는 "벡터"라고 불립니다.

For finite dimensions, V is always equivalent to Kn, with n a natural number, and n is called the "dimension" of V .

유한 차원의 경우, V는 항상 자연수 n을 가진 Kn과 동등하며, n은 V의 "차원"이라고 합니다.

This means that in finite dimensions, V can ALWAYS be understood as a list/array/tuple containing n elements of K.

이는 유한 차원에서 V를 항상 K의 n개 요소를 포함하는 목록/배열/튜플로 이해할 수 있음을 의미합니다.

This also means that every field K can be understood as a 1D vector space.

이것은 또한 모든 필드 K가 1차원 벡터 공간으로 이해될 수 있음을 의미합니다.

We generally denote vectors with Latin letters.

우리는 일반적으로 벡터를 라틴 문자로 나타냅니다.

An operation, called scalar multiplication (or scaling multiplication), which allows us to combine elements of K and V.

K와 V의 요소를 결합할 수 있는 "스칼라 곱셈"(또는 스케일링 곱셈)이라고 하는 연산입니다.

We can’t add or subtract an element of K with an element of V , but we can multiply an element of K and an element of V , which returns an element of V.

K의 요소와 V의 요소를 더하거나 빼는 것은 불가능하지만, K의 요소와 V의 요소를 곱할 수 있으며, 이는 V의 요소를 반환합니다.

The operation of scalar multiplication must also fullfill the following properties:

스칼라 곱셈 연산은 다음 속성을 충족해야 합니다.

Scalar multiplication takes two elements, one in K, one in V , and returns an element of $$V : λ ∈ K, ∀u ∈ V, λu ∈ V$$

스칼라 곱셈은 두 개의 요소(K의 하나, V의 하나)를 취하고 V의 요소를 반환합니다: $$V : λ ∈ K, ∀u ∈ V, λu ∈ V$$

> 수식은 다음과 같은 의미를 가집니다:
> 
> - **λ ∈ K**: 람다(λ)는 집합 K의 원소입니다. 여기서 K는 아마도 함수들의 집합을 나타낼 것입니다.
> - **∀u ∈ V**: 모든 u가 집합 V의 원소인 경우에 대해 다음이 성립합니다. (∀는 "모든"을 의미하는 논리 기호입니다.)
> - **λu ∈ V**: 람다(λ)와 u의 곱 또는 조합(함수 적용 등)은 집합 V의 원소입니다.
> 
> **전체적인 의미:**
> 
> 이 수식은 특정 함수(λ)가 어떤 벡터 공간(V)에 작용할 때, 그 결과도 항상 같은 벡터 공간(V) 안에 있다는 것을 나타냅니다. 즉, 람다는 K에서 가져왔지만, V의 원소와 결합하면 V의 원소를 반환하는 함수라는 의미입니다.

Pseudo-distributivity on vectors (look up "distributivity"): $$∀λ ∈ K, ∀(u, v) ∈ V^2, λ(u + v) = λu + λv$$

벡터에 대한 유사 분포성(“분포성”을 찾아보세요): $$∀λ ∈ K, ∀(u, v) ∈ V^2, λ(u + v) = λu + λv$$

> - **의미:** 이 수식은 _분배 법칙_을 나타냅니다. K에 속하는 모든 스칼라(λ)에 대해, V 공간의 임의의 두 벡터(u, v)에 대해, 스칼라를 벡터의 합에 곱하는 것은 각 벡터에 스칼라를 곱한 후 더하는 것과 같습니다.
> - **설명:** 쉽게 말해, "스칼라는 벡터들의 덧셈에 대해 분배된다"는 뜻입니다. 이는 선형 변환의 핵심적인 성질 중 하나입니다.

Pseudo-distributivity on scalars (look up "distributivity"): $$∀(λ, μ) ∈ K2, ∀u ∈ V, (λ + μ)u = λu + μu$$

스칼라에 대한 유사 분포성(“분포성”을 찾아보세요): $$∀(λ, μ) ∈ K2, ∀u ∈ V, (λ + μ)u = λu + μu$$

> - **의미:** 이 수식은 _스칼라 곱셈의 결합 법칙_을 나타냅니다. K 공간의 임의의 두 스칼라(λ, μ)에 대해, V 공간의 임의의 벡터(u)에 대해, 두 스칼라의 합에 벡터를 곱하는 것은 각 스칼라에 벡터를 곱한 후 더하는 것과 같습니다.
> - **설명:** "두 개의 스칼라를 더해서 하나의 스칼라로 만든 다음, 그 스칼라를 벡터에 곱하는 것과 각각의 스칼라를 벡터에 곱한 뒤 더하는 것은 같은 결과이다"라는 의미입니다.

Multiplicative pseudo-associativity of scalar multiplication (look up "associativity"): $$∀(λ, μ) ∈ K2, ∀u ∈ V, (λμ)u = λ(μu)$$

스칼라 곱셈의 승수 유사 결합성 (“결합성”을 찾아보세요): $$∀(λ, μ) ∈ K2, ∀u ∈ V, (λμ)u = λ(μu)$$