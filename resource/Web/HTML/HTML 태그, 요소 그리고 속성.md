
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



---

참고자료

#참고도서/모던_웹_디자인을_위한_HTML5_CSS3_입문 

---