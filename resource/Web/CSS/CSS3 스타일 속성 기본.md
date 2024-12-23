
---

#language/css #web 

*visual studio에서 Ctrl + Spacebar로 스타일 속성 선택지를 확인할 수 있으므로 미련하게 꾸역꾸역 외우지 말자*

---

#  CSS3 단위

스타일 속성은 아래의 코드처럼 입력한다. 이때 오른쪽에 입력하는 값은 특정한 단위를 갖는다. 이 절에서는 스타일시트에서 사용하는 단위를 알아본다.

```html

<style>
	h1 {
		margin: 10px;
		font-size: 200%;
		line-height: 2em;
	}
</style>

```

## 키워드

키워드는 CSS3에서 가장 쉽게 사용할 수 있는 단위이다. 각각의 스타일 속성에 따라 별도의 키워드가 존재한다.

## 크기 단위

크기 단위는 CSS3에서 가장 많이 사용하는 단위이다. CSS3에서 사용하는 크기 단위는 **%, em, cm, mm, inch, px**이다. 이중에서 자주 사용하는 크기 단위는 아래와 같다.

| 단위 | 설명        |
| ---- | ----------- |
| %    | 백분율 단위 |
| em   | 배수 단위   |
| px   | 픽셀            |

첫번째로 알아볼 단위는 퍼센트 단위이다. 퍼센트 단위는 기본 설정된 크기에서 상대적으로 크기를 지정한다. 100%가 초기에 설정된 크기이다.

```html

<!--percent.html-->

<!DOCTYPE html>
<html>
	<head>
		<title>CSS3 Style Property Basic</title>
		<style>
			p:nth-child(1) { font-size: 0% }
			p:nth-child(2) { font-size: 100% }
			p:nth-child(3) { font-size: 150% }
			p:nth-child(4) { font-size: 200% }
		</style>
	</head>
	<body>
		<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
		<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
		<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
		<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
	</body>
</html>

```

두번째로 알아볼 크기 단위는 em 단위이다. em 단위는 배수를 나타내는 단위이다. 1배=1em=100%이며 1.5배=1.5em=150%이다.

```html

<!--percent.html-->

<!DOCTYPE html>
<html>
	<head>
		<title>CSS3 Style Property Basic</title>
		<style>
			p:nth-child(1) { font-size: 0.0em; }
			p:nth-child(2) { font-size: 1.0em; }
			p:nth-child(3) { font-size: 1.5em; }
			p:nth-child(4) { font-size: 2.0em; }
		</style>
	</head>
	<body>
		<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
		<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
		<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
		<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
	</body>
</html>
```

% 단위와 em 단위는 모두 상대적으로 크기를 지정한다. 절대적으로 크기를 지정할 때는 px 단위를 사용한다. 참고로 p 태그의 기본 font-size 속성이 16픽셀이다.

```html

<!--percent.html-->

<!DOCTYPE html>
<html>
	<head>
		<title>CSS3 Style Property Basic</title>
		<style>
			p:nth-child(1) { font-size: 0px; }
			p:nth-child(2) { font-size: 16px; }
			p:nth-child(3) { font-size: 24px; }
			p:nth-child(4) { font-size: 32px; }
		</style>
	</head>
	<body>
		<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
		<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
		<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
		<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
	</body>
</html>

```

### 크기 단위의 복합 사용

폰트 크기를 지정할 때는 크기 단위를 섞어서 사용하는 경우가 많다. 이번에는 크기 단위를 섞어서 사용하는 방법을 살펴보자.

아래의 코드는 절대 크기 단위와 상대 크기 단위를 섞어서 폰트 크기를 지정한다.

```html

<!--combined.html-->

<!DOCTYPE html>
<html>
	<head>
		<title>CSS3 property Basic</title>
		<style>
			* { font-size:12px; }
			h1 { font-size:3.0em; }
			h2 { font-size:1.5em; }
		</style>
	</head>
	<body>
		<h1>Lorem ipsum dolor sit amet</h1>
		<h2>consectetur adipiscing elit. Sed nec purus elit, nec cursus dolor.</h2>
		<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed nec purus elit.</p>
	</body>
</html>

```

전체 폰트 크기에 절대 크기를 지정하고 각각의 태그에 상대 크기를 지정하는 방법은 많이 사용되므로 기억하는 것이 좋다.

### 제로

크기 단위 0을 입력하는 경우 단위를 입력하지 않아도 된다. 개발자의 취향에 따라서 0을 입력하는 경우에도 단위를 표기하는 경우가 있고 표기하지 않는 경우도 있다.

## 색상 단위

색상을 입력하는 가장 간단한 방법은 아래의 코드처럼 키워드를 입력하는 것이다.

```html

<style>
	h1 { background-color: red; }
	h2 { background-color: orange; }
	h3 { background-color: blue; }
	h4 { background-color: green; }
	h5 { background-color: brown; }
	h6 { background-color: purple; }
<\style>

```

하지만 단어로 표현할 수 있는 색상은 제한되어 있으므로 더욱 다양한 색상 표현을 위해 아래의 표와 같은 색상 단위를 제공한다.

| 단위 형태                               | 설명           |
| --------------------------------------- | -------------- |
| \#000000                                | HEX 코드 단위  |
| rbg(red, green, blue)                   | RGB 색상 단위  |
| rbga(red, green, blue, alpha)           | RGBA 색상 단위 |
| hsl(hue, saturation, lightness)         | HSL 색상 단위  |
| hsla(hue, saturation, lightness, alpha) | HSLA 색상 단위 |

> ## 알파 값
> RGBA와 HSLA의 A는 투명도를 의미하는 알파 값이다. 알파 값은 0.0부터 1.0 사이의 숫자를 입력한다. 0.0을 입력할 경우에는 완전히 투명한 상태를 나타내고 1.0을 입력할 경우에는 불투명한 상태를 나타낸다.

rgb 단위는 red, green, blue의 조합을 사용하여 색상을 표현하는 단위이다.
RGB 색상은 다음과 같이 사용한다. 각각의 숫자는 0부터 255까지 입력할 수 있다.

```html

<style>
	h1 { background-color: rgb(255,255,255); }
<\style>

```

HEX 코드 단위는 RGB 색상 단위를 짧게 입력하는 방법이다. HEX 코드는 16진수로 RGB 색상 조합을 순서대로 입력한다.

```html

<style>
	h1 { background-color: #0094FF;}
<\style>

```

HSL 색상은 색상 Hue, 채도 Saturation, 명도 Lightness를 사용한다.
아래와 같이 입력한다.

```html

<style>
	h1 { background-color: hsl(33, 100%, 50%);}
<\style>

```

## URL 단위

CSS3에서 이미지 파일이나 폰트 파일을 불러올 때는 URL 단위를 사용한다. 간단히 아래의 예제를 통해서 URL 단위의 사용법에 대해서 알아보자.

```html

<!--url.html-->

<!DOCTYPE html>
<html>
	<head>
		<title>CSS3 property Basic</title>
		<style>
			body {
				background-image: url('Desert.jpg');
			}
		</style>
	</head>
	<body>
		<h1>Lorem ipsum dolor amet.</h1>
		<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
	</body>
</html>

```

url() 함수 내부에 경로를 입력하면 된다. URL 경로를 입력할 때는 아래처럼 복잡한 경로를 사용할 수 있다.

```html

/* 현재 폴더의 Desert.jpg */
background-image: url('Desert.jpg');

/* 현재 폴더 내부의 Other 폴더의 Desert.jpg */
background-image: url('Other/Desert.jpg');

/* 루트 폴더의 Desert.jpg */
/* 루트 폴더의 개념은 서버를 알아야 한다 */
background-image: url('/Desert.jpg');

```

## 가시 속성

가시 속성은 태그가 화면에 보이는 방식을 지정하는 속성이다.

### display 속성

display 속성 중 주로 사용되는 속성으로는 다음이 있다.

| 키워드 이름  | 설명                                   |
| ------------ | -------------------------------------- |
| none         | 태그를 화면에서 보이지 않게 만든다.    |
| block        | 태그를 block 형식으로 지정한다.        |
| inline       | 태그를 inline 형식으로 지정한다.       |
| inline-block | 태그를 inline-block 형식으로 지정한다. |

다음은 위의 표 중 none 키워드를 사용한 예제이다. 다른 키워드를 사용할 땐 display의 키워드를 변경해주면 된다.

```html

<!--none.html-->

<!DOCTYPE html>
<html>
	<head>
		<title>CSS3 Style Property Basic</title>
		<style>
			#box {
				display: none;
			}
		</style>
	</head>
	<body>
		<span>Dummy</span>
		<div id="box">
			<span>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</span>
		</div>
		<span>Dummy</span>
	</body>
</html>

```

코드를 실행했을 때, 단순히 보기에는 inline 형식과 inline-block 형식 모두 동일하게 출력되는 듯 하다.

하지만 width 속성과 height 속성, maring 속성을 사용할 때 2가지 형식의 차이를 확인할 수 있다.

```html

<!--inline.html-->

<!DOCTYPE html>
<html>
	<head>
		<title>CSS3 Style Property Basic</title>
		<style>
			#box {
				display: inline;

				background-color: red;
				width: 300px; height: 50px;
				margin: 10px;
			}
		</style>
	</head>
	<body>
		<span>Dummy</span>
		<div id="box">
			<span>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</span>
		</div>
		<span>Dummy</span>
	</body>
</html>

```

```html

<!--inline-block.html-->

<!DOCTYPE html>
<html>
	<head>
		<title>CSS3 Style Property Basic</title>
		<style>
			#box {
				display: inline-block;

				background-color: red;
				width: 300px; height: 50px;
				margin: 10px;
			}
		</style>
	</head>
	<body>
		<span>Dummy</span>
		<div id="box">
			<span>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</span>
		</div>
		<span>Dummy</span>
	</body>
</html>

```

inline 키워드를 적용한 코드는 width 속성과 height 속성이 적용되지 않는다. 또한 margin 속성이 div 태그의 좌우로만 지정된다.

반면에 inline-block 키워드를 적용하면 width 속성과 height 속성을 적용할 수 있다. 또한 margin 속성이 상하좌우로 적용된다. 이러한 특징은 block 키워드와 동일하다.

### visibility 속성

visiblity 속성은 대상을 보이거나 보이지 않게 지정하는 스타일 속성이다. visibility 속성에는 다음과 같은 키워드들을 사용한다.

| 키워드 이름 | 설명                            |
| ----------- | ------------------------------- |
| visible     | 태그를 보이게 만든다            |
| hidden      | 태그를 보이지 않게 만든다       |
| collapse    | table 태그를 보이지 않게 만든다 |

위 절에서 살펴본 display 속성의 none 키워드도 대상을 화면에서 보이지 않게 만든다. 따라서 display 속성의 none 키워드와 visibility 속성의 hidden 키워드의 차이를 아는 것이 중요하다.

none 키워드를 사용하면 해당 블록이 완전히 사라지지만, hidden 키워드를 사용하면 해당 블록의 공간 자체는 남아있고 내용물만 보이지 않게 된다는 차이점이 있다.

> ## collapse 속성
> visibility의 다른 키워드인 hidden도 table에 적용하는 것이 가능하다. 하지만 hidden은 내용물을 보이지 않게 할 뿐 표의 공간 자체는 남아있는 반면, collapse 속성은 none과 같이 표 자체를 없애버린다는 차이점이 있다.

```html

<!--collapse.html-->

<!DOCTYPE html>
<html>
	<head>
		<title>CSS3 Selector Basic Page</title>
		<style>
			table {
				visibility: collapse;
			}
		</style>
	</head>
	<body>
		<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
		<table>
			<tr><td>TEST</td><td>Test</td></tr>
			<tr><td>TEST</td><td>Test</td></tr>
			<tr><td>TEST</td><td>Test</td></tr>
		</table>
		<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
	</body>
</html>

```

### opacity 속성

opacity 속성은 태그의 투명도를 조절하는 스타일 속성이다. opacity 속성에는 0.0부터 1.0 사이의 숫자를 입력할 수 있으며 0.0은 완전히 투명한 상태를 나타내고 1.0은 완전히 불투명한 상태를 나타낸다.

예를 들어 아래처럼 0.2를 적용하면 약간 투명한 상태로 보인다.

```html

<!--opacity.html-->

<!DOCTYPE html>
<html>
	<head>
		<title>CSS3 Basic Page</title>
		<style>
			#box {
				background-color: black;
				color: white;

				opacity: 0.2;
			}
		</style>
	</head>
	<body>
		<div id="box">lorem ipsum dolor sit amet,
			consectetur adipiscing elit.
		</div>
	</body>
</html>

```

## 박스 속성

박스 속성은 웹 페이지의 레이아웃을 구성할 때 가장 중요한 스타일 속성이다. CSS는 다음과 같은 속성을 모두 합쳐 박스 속성이라고 이야기한다.

- margin
- border
- padding
- height
- width

---

참고자료

#참고도서/모던_웹_디자인을_위한_HTML5_CSS3_입문 

---