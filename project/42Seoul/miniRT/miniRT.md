
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

| 프로그램 이름  | miniRT                                                                 |
| -------------- | ---------------------------------------------------------------------- |
| 제출 파일      | 구현한 모든 파일                                                       |
| Makefile       | all, clean, fclean, re, bonus                                          |
| 인자           | 씬 정보를 담고 있는 \*.rt 파일                                         |
| 허용함수       | open, close, read, write, printf, malloc, free, perror, strerror, exit |
|                | math 라이브러리의 모든 함수 (-lm man man 3 math 참고)                  |
|                | MinilibX의 모든 함수                                                   |
| Libft 허용여부 | Yes                                                                    |
| 설명           | 프로그램의 목적은 Ray Tracing을 이용하여 이미지를 생성하는 것이다. 컴퓨터로 생성된 이미지는 특정 각도와 위치를                                                                        |