
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

사물의 크기 요소를 다시 설정할 수 있어야 한다: 원의 지름, 원기둥의 넓이 높이 등등.

Your program must be able to apply translation and rotation transformation to objects, lights and cameras (except for spheres and lights that cannot be rotated)

사물, 광원, 카메라의 이동과 회전을 구현해야 한다 (구와 회전이 적용될 수 없는 광원은 예외)

Light management: spot brightness, hard shodows, ambiance lighting (objects are never completely in the dark). You must implement Ambient and diffuse lighting.

광원 관리 : 점 광원 밝기, hard shadows(그림자의 경계가 명확하게 끊어지는 렌더링 기법), 환경광 Ambiance lighting(사물이 완전히 검게 물드는 부분이 없어야 함). 당신은 환경광과 난반사를 구현해야 한다.

The program displays the image in a window and respect the following rules:
- Pressing Esc must close the window and quit the program cleanly.
- Clicking on the red cross on the window's frame must close the window and uit the program cleanly.
- The use of images of the minilibX is strongly recommanded.

프로그램은 창에 이미지를 띄워야 하며 다음의 규칙을 따라야 한다.
- Esc를 누르면 창이 닫히고 프로그램이 종료되어야 한다.
- 창의 틀에 있는 빨간 십자 버튼을 누르면 창이 닫히고 프로그램이 종료되어야 한다.
- minilibX의 이미지를 사용하는 것이 강력하게 권장된다.

Your program must take as a first argument a scene description fiie with the .rt extension.
- Each type of element can be seperated by one or more line break(s).
- Each type of imformation from an element can be separated by one or more space(s).
- Each type of element cat be set in any order in the file.
- Elements which are defined by a capital letter can only be declared once in the scene.

프로그램은 .rf 확장자를 가진, 장면을 정의하는 파일을 첫번째 인자로 받아야 한다.
- 각각의 요소는 하나 이상의 개행으로 분리되어야 한다.
- 요소로부터 비롯된 각각의 속성은 하나 이상의 공백으로 분리되어야 한다.
- 각각의 요소는 파일의 어떠한 위치에도 존재할 수 있다.
- 대문자로 정의되는 요소들은 하나의 장면에 하나만 존재할 수 있다.

Each element first’s information is the type identifier (composed by one or two character(s)), followed by all specific information for each object in a strict order such as:

요소의 첫번째 속성은 타입 정의자(하나 혹은 두 개의 문자로 구성된다)이며, 그 뒤의 속성들은 사물의 정보를 아래와 같이 구체적으로 명시해야 한다:

---

Ambient lightning:

`A 0.2 255,255,255`

+ identifier: A
+ ambient lighting ratio in range \[0.0, 1.0]: 0.2
+ R,G,B colors in range \[0-255]: 255, 255, 255

환경광:

`A 0.2 255,255,255`

+ 식별자: A
+ 환경광 비율(\[0.0, 1.0]의 범위를 가진다.): 0.2
+ R,G,B 색상(\[0-255]의 범위를 가진다.): 255, 255, 255

---

Camera:

`C -50.0,0,20 0,0,1 70`

+ identifier: C
+ x,y,z coordinates of the view point: -50.0,0,20
+ 3d normalized orientation vector. In range \[-1, 1] for each x,y,z axis: 0.0,0.0,1.0
+ FOV : Horizontal field of view in degrees in range \[0,180]: 70

카메라:

`C -50.0,0,20 0,0,1 70`

+ 식별자: C
+ 시점 veiw point의 x, y, z 좌표값 : -50.0, 0, 20
+ 정규화된 3차원 방향 벡터. x, y, z 축 모두 \[-1, 1] 범위를 가진다.
+ FOV : 수평 시야각. (\[0, 180] 사이의 범위를 가지고 있다.) : 70

---

Light:

`L -40.0,50.0,0.0. 0.6  10,0,255`

+ identifier: L 
+ x,y,z coordinates of the light point: -40.0,50.0,0.0
+ the light brightness ratio in range \[0.0,1.0]: 0.6
+ (unused in mandatory part)R,G,B colors in range \[0-255]: 10, 0, 255

광원:

`L -40.0,50.0,0.0. 0.6  10,0,255`

+ 식별자: L
+ 광원의 x, y, z 좌표: -40.0,50.0,0.0
+ 빛의 밝기 비율. (\[0.0,1.0]의 범위를 가짐): 0.6
+ (mendatory part에서는 사용되지 않음)R,G,B 색상 (\[0-255]의 범위를 가짐): 10, 0, 255

---

Sphere:

`sp 0.0,0.0,20.6 12.6 10,0, 55`

+ identifier: sp
+ x,y,z coordinates of the sphere center: 0.0,0.0,20.6
+ the sphere diameter: 12.6
+ R,G,B colors in range \[0-255]: 10, 0, 255

구:

`sp 0.0,0.0,20.6 12.6 10,0, 55`

+ 식별자: sp
+ 구의 중심의 x, y, z 좌표: 0.0,0.0,20.6
+ 구의 지름: 12.6
+ R,G,B 색상. (\[0-255] 사이의 범위를 가짐.): 10, 0, 255

---

Plane:

`pl 0.0,0.0,-10.0 0.0,1.0,0.0 0,0,255`

+ identifier: pl
+ x,y,z coordinates of a point in the plane: 0.0,0.0,-10.0
+ 3d normalized normal vector. In range \[-1,1] for each x,y,z axis: 0.0,1.0,0.0
+ R,G,B colors in range \[0-255]: 0,0,225

---

평면:

`pl 0.0,0.0,-10.0 0.0,1.0,0.0 0,0,255`

+ 식별자: pl
+ x,y,z 평면의 중점 좌표: 0.0,0.0,-10.0
+ 정규화된 3차원 법선 벡터 (x,y,z 축 좌표의 값은 \[-1,1] 범위를 가짐): 0.0,1.0,0.0
+ R,G,B 색상 범위 : 0,0,225

---

Cylinder:

`cy 50.0,0.0,20.6 0.0,0.0,1.0 14.2 21.42 10,0,255`

identifier: cy
x,y,z coordinates of the center of the cylinder: 50.0,0.0,20.6
3d normalized vector of axis of cylinder. In range [-1,1] for each x,y,z axis: 0.0,0.0,1.0
the cylinder diameter: 14.2
the cylinder height: 21.42
R,G,B colors in range [0,255]: 10, 0, 255