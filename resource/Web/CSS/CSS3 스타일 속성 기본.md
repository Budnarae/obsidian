
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
	h1 { background}
<\style>

```

---

참고자료

#

---