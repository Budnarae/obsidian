
---

#web #language/html

*tag*

---

# 태그와 요소

[[HTML | HTML5]] 페이지는 사용자에게 보이는 뷰와 사용자에게 보이지 않는 코드로 나누어진다.
지금부터 살펴볼 HTML 태그는 사용자에게 보이는 뷰를 만들 때 사용한다.

태그는 HTML 페이지에서 **객체**를 만들 때 사용한다. 그리고 태그를 사용해 만들어진 객체를 **요소 Element**라고 부른다.

```html

<h1>Hello TML5</h1>

```

HTML5은 위와 같이 시작 태그와 끝 태그를 별도로 입력하는 요소도 있지만 아래와 같이 시작 태그와 끝 태그를 함께 입력하는 요소도 존재한다.
이렇게 단독으로 사용하는 태그는 **HTML5 표기법**과 **XHTML5 표기법**을 사용해 입력한다.

왼쪽이 HTML5, 오른쪽이 XHTML5 표기법이다.

```html

<br><br/>

```

어떠한 표기법을 사용해도 상관없지만 대부분의 개발자는 XHTML5 방법을 선호한다.

일부 태그는 태그 내부에 다른 태그를 넣을 수도 있다.

```html

<article>
	<h1>Article Header</h1>
	<p>Lorem ipsum dolor sit amet.</p>
</article>

```

# 속성

태그에 추가 정보를 부여할 때는 속성을 사용한다.

아래의 예시에서 title이 **속성 이름**, header가 **속성 값**, 그리고 이 둘을 통틀어서 **속성 블록**이라 한다.
Hello HTML5는 **내부 문자**라고 한다.

```html

<h1 title="header">Hello HTML5</h1>

```

내부 문자를 갖지 않는 태그도 아래와 같이 속성을 사용할 수 있다.

```html

<img src="image.png"/>

```

# 태그 목록

## \<!DOCTYPE html> 태그

```html

<!DOCTYPE html>

```

모든 HTML 페이지의 첫 줄에 오는 태그이다. 웹 브라우저가 현재 웹 페이지가 HTML5 문서임을 인식하게 만들어준다.

W3C의 HTML5 명세에 따르면 모든 HTMl5 문서는 반드시 이 태그를 표기해야 한다.
또한 반드시 문서의 가장 첫 번째 줄에 있어야 한다.

## html 태그

모든 HTML 페이지의 **루트 요소**이다.
모든 HTML 페이지는 html 태그 내부에 작성할 수 있다.
html 태그에는 lang 속성을 입력할 수 있다.

```html

<html lang="ko">

```

lang 속성에는 다음과 같은 속성 값이 올 수 있다.

| 국가     | 속성값 |
| -------- | ------ |
| 한국     | ko     |
| 일본     | ja     |
| 중국     | zh     |
| 미국     | en     |
| 러시아어 | ru     |
| 독일어   | de       |

lang 속성은 실제 웹 브라우저가 동작하는 데 어떠한 영향도 끼치지 않는다. 대신 구글과 같은 검색 엔진이 웹 페이지를 탐색할 때 해당 웹 페이지가 어떤 언어로 만들어져 있는지 쉽게 인식하게 만든다.

전 세게적인 데이터 네트워크 구축을 위해서는 lang 속성을 입력하는 것이 좋다.

## head와 body 태그

body 태그는 사용자에게 보여지는 실제 부분이며, head 태그는 body 태그에서 필요한 스타일시트와 자바스크립트를 제공하는 데 사용한다.

### head 태그

head 태그 내부에는 다음 태그만 입력할 수 있다. 아래의 표 이외의 태그를 넣으면 웹 브라우저가 자동으로 해당 태그를 body 태그 내부로 옮긴다.

| 태그 이름 | 설명                              |
| --------- | --------------------------------- |
| meta      | 웹 페이지에 추가 정보를 전달한다  |
| title     | 웹 페이지의 제목                  |
| script    | 웹 페이지에 스크립트를 추가한다   |
| link      | 웹 페이지에 다른 파일을 추가한다  |
| style     | 웹 페이지에 스타일시트를 추가한다 |
| base      | 웹 페이지의 기본 경로를 지정한다.                                  |

## 글자 태그

### 제목 태그 - h 시리즈

HTML5의 대표적인 글자 태그는 제목을 입력할 때 사용하는 제목 글자 태그이다.
HTML5는 **h1 ~ h6**까지의 제목 글자 태그를 제공한다. h 뒤의 숫자는 글자의 크기 및 우선 순위를 나타낸다.

```html

<!--header.html-->

<!DOCTYPE html>
<html>
<head>
	<title>HTML5 + CSS3 TEXT</title>
</head>
<body>
	<h1>Header 1</h1>
	<h2>Header 2</h2>
	<h3>Header 3</h3>
	<h4>Header 4</h4>
	<h5>Header 5</h5>
	<h6>Header 6</h6>
</body>
</html>

```

### 단락 태그 - p

p 태그는 paragraph의 줄임말이다. paragraph는 단락을 의미하므로 p 태그를 사용하면 하나의 단락을 만들 수 있다.

```html

<!--paragraph.html-->

<!DOCTYPE html>
<html>
<head>
	<title>HTML TEXT Basic Page</title>
</head>
<body>
	<h1>Lorem ipsum</h1>
	<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
	<p>Nam commodo mi a lorem congue id rutrum leo venenatis.</p>
</body>
</html>

```

### 개행 태그 - br

`<br />`와 같이 사용한다. 줄바꿈을 적용한다.

### 수평 줄 태그 - hr

`<hr />`과 같이 사용한다. 수평 줄을 그린다.

```html

<!--paragraph.html-->

<!DOCTYPE html>
<html>
<head>
<title>HTML TEXT Basic Page</title>
</head>
<body>
	<h1>Lorem ipsum</h1>
	<h2>dodor sit amet</h2>
	<hr />
	<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
	<br />
	<p>Nam commodo mi a lorem congue id rutrum leo venenatis.</p>
</body>
</html>

```

## 앵커 태그 - a

앵커 anchor 태그는 서로 다른 웹 페이지 사이를 이동하거나 웹 페이지 내부에서 특정한 위치로 이동할 때 사용되는 태그이다.

**href** 속성을 사용하여 이동하고자 하는 웹페이지를 정확히 지정해야 제대로 작동한다.

```html

<!--anchor.html-->

<!DOCTYPE html>
<html>
<head>
	<title>HTML TEXT BASIC PAGE</title>
</head>
<body>
	<a href="http://hanbit.co.kr">Hanbit</a><br />
	<a href="https://github.com/">GitHub</a><br />
</body>
</html>

```

### 빈 링크

a 태그는 본래 가지고 있는 하이퍼링크 기능을 제거하고 사용하는 경우도 있다. 하지만 하이퍼링크 기능을 제거해도 웹 표준을 따르려면 a 태그에 href 속성을 반드시 입력해야 한다. 따라서 웹 표준을 지키면서 이동하지 않는 a 태그를 만들 때는 href속성에 \#을 입력한다. 그리고 이를 빈 링크라고 부른다.

```html

<a href="#">Empty link</a>

```

### 페이지 내부 이동

a 태그를 이용하면 현재 페이지 내부에서 원하는 장소로 이동할 수 있다. 이때는 원하는 장소에 id 속성을 부여해야 한다. 코드 2-8처럼 이동하기를 원하는 태그에 id 속성을 부여하고 a 태그의 href 속성에 **\#아이디** 형태의 문자열을 입력한다.

```html

<!--id.html-->

<!DOCTYPE html>
<html>
<head>id.html</head>
<body>
	<a href="#alpha">Move to Alpha</a>
	<a href="#beta">Move tot Beta</a>
	<a href="#gamma">Move to Gamma</a>
	<hr />
	<h1 id="alpha">Alpha</h1>
	<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
	<h1 id="beta">Beta</h1>
	<h1 id="gamma">Gamma</h1>
	<p>Nullam porta, felis sit amet porttitor vestibulum.</p>
</body>
</html>

```

id 속성이 중복되면 먼저 나오는 태그로 이동한다. 하지만 id 속성을 중복해서 사용하는 것은 웹 표준에 어긋나는 행위이므로 지양해야 한다.

## 글자 형태

HTML5는 글자 형태 태그를 사용해 웹페이지의 글자와 형태에 의미를 부여한다. 각 글자에 형태 및 의미를 부여할 때는 아래의 표이 태그들을 사용한다.

| 태그 이름 | 설명                         |
| --------- | ---------------------------- |
| b         | 굶은 글자 태그               |
| i         | 기울어진 글자 태그           |
| small     | 작은 글자 태그               |
| sub       | 아래에 달라 붙는 글자 태그   |
| sup       | 위에 달라 붙는 글자 태그     |
| ins       | 밑줄 글자 태그               |
| del       | 가운데 줄이 그어진 글자 태그 |

```html

<!--letter_type.html-->

<!DOCTYPE html>
<html>
<head>
	<title>HTML TXT Basic Page</title>
</head>
<body>
	<h1><b>Lorem ipsum dolor sit amet</b></h1>
	<h1><i>Lorem ipsum dolar sit amet</i></h1>
	<h1><small>Lorem ipsum dolar sit amet</small></h1>
	<h1><sub>Lorem ipsum dolar sit amet</sub></h1>
	<h1><sup>Lorem ipsum dolar sit amet</sup></h1>
	<h1><ins>Lorem ipsum dolar sit amet</ins></h1>
	<h1><del>Lorem ipsum dolar sit amet</del></h1>
	<hr />
	<b>Lorem ipsum dolor sit amet</b><br />
	<i>Lorem ipsum dolor sit amet</i><br />
	<small>Lorem ipsum dolor sit amet</small><br />
	<sub>Lorem ipsum dolor sit amet</sub><br />
	<sup>Lorem ipsum dolor sit amet</sup><br />
	<ins>Lorem ipsum dolor sit amet</ins><br />
	<del>Lorem ipsum dolor sit amet</del><br />
</body>
</html>

```

과거에는 이 절의 태그를 많이 사용하였다. 하지만 글자를 기울이거나 굵게 만드는 기능은 모두 스타일시트로 처리하므로 현대에는 잘 사용하지 않는다.

## 루비 문자

(생략)

## 목록 태그

대부분의 웹페이지에서 자주 사용되는 기능 중 하나는 메뉴 기능이다. 일반적으로 페이지를 이동할 때 사용되는 메뉴를 **내비게이션 메뉴**라고 한다.

내비게이션 메뉴를 만들 때는 아래의 목록 태그들을 활용한다.

| 태그 이름 | 설명                  |
| --------- | --------------------- |
| ul        | 순서가 없는 목록 태그 |
| ol        | 순서가 있는 목록 태그 |
| li        | 목록 요소             |

ol 태그는 **정렬된 목록 ordered list**를 의미하고
ul 태그는 **정렬되지 않은 목록 unordered list**를 의미한다.
li 태그는 **목록 요소 list item**를 의미한다.

```html

<!--basic_list.html-->

<!DOCTYPE html>
<html>
<head>HTML Basic Page</head>
<body>
	<h1>ol tag</h1>
	<ol>
		<li>Facebook></li>
		<li>Tweeter></li>
		<li>Linked In</li>
	</ol>
	<h1>ul tag</h1>
	<ul>
		<li>Facebook</li>
		<li>Tweeter></li>
		<li>Linked in</li>
	</ul>
</body>
</html>

```

### 중첩 목록

중첩해서 목록을 만들고 싶을 때는 li 태그 안에 목록 태그를 중첩해서 입력한다.

```html

<!--list_in_list.html-->

<!DOCTYPE html>
<html>
	<body>
	<ul>
		<li>HTML5
			<ol>
				<li>Multimedia Tag</li>
				<li>Connectivity</li>
				<li>Device Access</li>
			</ol>
		</li>
		<li>CSS3
			<ul>
				<li>Animation</li>
				<li>3D Transform</li>
			</ul>
		</li>
	</ul>
	</body>
</html>

```

## 테이블 태그

**table** 태그는 HTML 페이지에서 표를 만들 때 사용하는 태그이다. 과거에는 테이블 태그를 사용해 레이아웃을 구성하였다. 하지만 현대 웹 페이지의 대부분은 후술할 div 태그를 사용해 레이아웃을 구성하므로 사용 빈도가 굉장히 줄었다.

---

참고자료

#참고도서/모던_웹_디자인을_위한_HTML5_CSS3_입문 

---