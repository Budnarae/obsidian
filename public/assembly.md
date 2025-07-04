
---

#language/asm 

_assembly tutorial_

---

# 개요

**어셈블리 언어**는 컴퓨터 언어의 일종으로 명령어와 기계어를 1:1로 매핑시킬 수 있는 가장 저 레벨의 언어이다.

어셈블리 언어는 CPU, 레지스터, 메모리 사이에 데이터를 조작하는 것을 주로 한다. 어셈블리에서 사용하는 명령어는 전통적으로 **instruction**이라 하며, CPU에 내장되어 있다. 이외에도 컴퓨터의 하드웨어 제어를 위해 컴퓨터 메인보드에 **롬 바이오스**라는 미리 내장되어 있는 API도 사용이 가능하다.

CPU가 지원하는 insturction만으로 프로그램을 구성하는 것은 너무 고통스러운 일이기 때문에, 보통 운영체제가 지원하는 고급(어디까지나 CPU의 insturction에 비해서) 함수를 사용하게 된다. 물론 이러한 고급 함수도 내부적으로는 CPU 또는 롬 바이오스의 API로 만들어진 것이다. 

운영체제는 CPU를 비롯한 컴퓨터의 모든 리소스를 관리하기 때문에 운영체제가 정해놓은 규칙을 준수하는 바이너리만 해당 운영체제에서 실행이 가능하다. 따라서 어셈블리 소스는 실행할 운영체제가 무엇인가에 따라 코드가 달라지게 된다. 이는 여러 플랫폼 간 이식성을 제공하는 고수준 언어와 대비되는 어셈블리어의 특징이다.

# 어셈블러와 링커

어셈블리 언어로 작성된 소스를 해당 기계에서 실행 가능하게 바이너리(기계어)로 변환하는 프로그램을 **어셈블러(assembler)**라고 한다.

어셈블러에 의해 만들어진 바이너리가 실행되려면 1차 기계어로 만들고 2차 필요한 라이브러리를 모두 저 레벨 함수로 결합하는 링킹 기능이 필요한데, 이러한 기능을 하는 것이 **링커(linker)**이다.

# 어셈블러와 개발 환경

어셈블리 언어로 프로그래밍하는 것은 고급 언어에 비해 규칙이 매우 단순하며 반복적인 부분이 많다. 이런 이유로 편의를 위해 내부적으로 많은 매크로를 사용하게 되는데, 이러한 매크로는 사용하는 어셈블러에 따라 다르다. 이러한 매크로의 차이에 의해 서로 다른 어셈블러는 소스 호환이 되지 않는 문제가 발생한다.

이러한 혼란을 조금이라도 줄이고자 이 문서는 윈도우, 유닉스/리눅스 계열(맥 포함)에서 공통으로 동작하는 NASM이라는 어셈블러를 기준으로 작성되었다.

# 어셈블리 언어 표기법

어셈블리 언어에서 사용하는 문법 표기는 **인텔 표기법**과 **AT & T 표기법**이 그것이다.

==인텔 표기법==

```asm

mov eax, 3

```

==AT & T 표기법==

```asm

mov $3, %eax

```

이 문서는 인텔 표기법을 기준으로 작성되었다.

# 데이터 단위

| 단위 | 바이트 |
| ---- | ------ |
| byte | 1      |
| word | 2      |
|      |        |
