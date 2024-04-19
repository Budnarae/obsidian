
---

#42Seoul #graphics

*ray tracing*

---

#### I. 개요 Introduction

When it comes to rendering 3-dinemsional computer-generated images there are 2 possible approaches: "Rasterization", which is used by almost all graphic engines because of its efficiency and "Ray Tracing"

컴퓨터로 3차원 이미지를 렌더링하는 방식은 2가지가 있다. 첫번째는 효율성 때문에 대부분의 그래픽 엔진에 의해 사용되는 Rasterization이다. 두번째는 Ray Tracing이다.

The "Ray Tracing" method, developed for the first time in 1968 (but improved upon since) is even today more expensive in computation than the "Rasterization" method.

Ray Tracing 기법은 1968년에 처음 고안되었고, 큰 발전을 거듭했음에도 Rasterization 방법에 비해 훨신 많은 연산이 필요하다.

As a result, it is not yet fully adapted to real time use-cases but it produce a much higher degree of visual realism.

결과적으로, Ray Tracing은 실시간으로 무언가를 투영해야 하는 경우에는 아직 적합하지 않지만, 훨씬 시각적으로 사실적인 표현이 가능하다.

Before you can even begin to produce such high-quality grapics, you must master the basics: the miniRT is your first ray tracer coded in C, normed and humble but functional.

높은 품질의 그래픽을 구현하기 전에, 당신은 우선 기초를 숙달해야 한다: miniRT는 C 언어로 짜인 당신의 표준적이고, 소박하지만 기능적인 첫번째 광선 추적기가 될 것이다.

The main goal of miniRT is to prove to yourself that you can implement any mathematics or physics formulas without being a mathematician, we will only implement the most basic ray tracing features here so just keep calm, take a deep breath and don't panic! After this project you'll be able to show off nice-looking pictures to justify the number of hours you're spending at school...

miniRT 과제의 주목적은 수학 그리고 물리 공식을 구현할 수 있음을 스스로에게 증명하는 것이다. 우리는 가장 기초적인 Ray Tracing의 특징만을 구현할 것이므로 너무 겁먹지 말라. 이번 프로젝트가 끝나면 여러분이 얼마나 많은 시간을 노력했는지 증명할 멋진 이미지를 얻을 것이다.

#### II. Common Instructions(생략)

#### III. Mandatory part - miniRT

| 프로그램 이름  | miniRT                                                                                                                                                                                                                                            |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 제출 파일      | 구현한 모든 파일                                                                                                                                                                                                                                  |
| Makefile       | all, clean, fclean, re, bonus                                                                                                                                                                                                                     |
| 인자           | 씬 정보를 담고 있는 \*.rt 파일                                                                                                                                                                                                                    |
| 허용함수       | open, close, read, write, printf, malloc, free, perror, strerror, exit                                                                                                                                                                            |
|                | math 라이브러리의 모든 함수 (-lm man man 3 math 참고)                                                                                                                                                                                             |
|                | MinilibX의 모든 함수                                                                                                                                                                                                                              |
| Libft 허용여부 | Yes                                                                                                                                                                                                                                               |
| 설명           | 프로그램의 목적은 Ray Tracing을 이용하여 이미지를 생성하는 것이다. 컴퓨터로 생성된 이미지는 특정 각도와 위치를 기준으로 투영된 장면 Scene을 나타내며, 그 장면은 간단한 기하학적 도형으로 구성된다. 또한 독자적인 lighting system을 구현해야 한다. |

The constraints are as follows:

다음의 제약을 따라야 한다.

You must use the **miniLibX**. Either the version that is available on the operatiing system, or from its sources. If you choose to work with the sources, you will need to apply the same rules for your **libft** as those written above in **Common Instructions** part.

반드시 **miniLibX**를 사용해야 한다. 운영체제에 설치되어 있는 버전을 써도 되고, 소스 파일을 다운받아 사용해도 된다. 만약 소스 파일을 다운받는다면, **Common Instructions**에 기술된 **libft**의 사용규칙을 그대로 적용해야 한다.

The management of your window must remain fluid: switching to another window, minimization, ect..

프로그램 창의 관리는 유동적이어야 한다: 다른 창으로의 전환, 최소화 등등이 적용되야 한다는 뜻.

When you change the resolution of the window, the content of the window must remain unchanged and be adjusted accordingly.

화면의 해상도를 바꿀 때, 화면의 구성은 그대로 유지한 채 보정만을 적용해야한다.

You need at least these 3 simple geometric objects: plane, sphere, cylinder.

적어도 3개의 간단한 기하학적 사물을 배치해야 한다: 평면, 구, 원기둥.

If applicable, all possible intersections and the inside of the object must be handled correctly.

사물 간의 중첩과 도형의 내부를 잘 제어할 수 있어야 한다.

Your program must be able to resize the object's unique properties: diameter for a sphere and the width and height for a cylinder.

