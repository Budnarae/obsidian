
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

Before you can even begin to produce such high-quality grapics, you must master the basics: the miniRT is your first ray tracer coded in C, normed and humble but
