
---

#web #language/css

**

---

# 선택자란?

**CSS3 선택자**는 특정한 HTML 태그를 선택할 때 사용하는 기능이다.

선택자를 사용해 특정한 HTML 태그를 선택하면 해당 태그에 우리가 원하는 스타일 또는 기능을 적용할 수 있다.

선택자는 다음과 같이 사용된다.

```css

h1{color:read;}

```

위 예제에서 각각의 요소는

- h1 : 선택자
- color : 스타일 속성
- red : 스타일 값

에 해당한다.

이러한 코드를 **CSS 블록**이라고 부르며 **style 태그** 내부에 입력해 사용한다. 이때 style 태그 내부에 입력되는 코드를 스타일시트라고 부른다.

```html

<!--stylesheet.html-->

<!DOCTYPE html>
<html>
	<head>
		<title>CSS Selector Basic</title>
		<style>
			h1 {
				color: red;
				background-color: orange;
			}
		</style>
	</head>
	<body>
		<h1>CSS Selector Basic</h1>
	</body>
</html>

```

CSS3 선택자는 다양한 종류로 이루어져 있다.

# 선택자의 종류

## 전체 선택자

HTML 문서 안의 모든 태그를 선택할 때는 전체 선택자를 사용한다.

| 선택자 형태 | 설명                                     |
| ----------- | ---------------------------------------- |
| \*          | HTML 페이지 내부의 모든 태그를 선택한다. |

전체 선택자는 모든 웹 페이지에서 빠지지 않고 사용하는 선택자이다.
아래의 코드는 전체 선택자를 사용해 모든 태그의 color 속성에 red 키워드를 적용한다.

```html

<!--select_all.html-->

<!DOCTYPE html>
<html>
	<head>
		<title>CSS3 Selector Basic Page</title>
		<style>
			/* 모든 태그의 color 속성에 red 키워드를 적용한다. */
			* { color: red; }
		</style>
	</head>
	<body>
		<h1>Lorem ipsum</h1>
		<p>lorem ipsum dolor sit amet, consectetur adipscing elit.</p>
	</body>
</html>

```

### 전체 선택자의 범위

일반적으로 전체 선택자를 사용하면 body 태그 내부에 있는 요소에만 스타일 속성이 적용되는 것처럼 보인다. 그래서 전체 선택자가 body 태그 내부에 있는 모든 요소를 선택한다고 생각하기 쉽다.

하지만 전체 선택자를 사용하면 html 태그를 포함해 head 태그, title 태그, style 태그까지 선택한다. 다음 예제는 jQuery를 사용해 전체 선택자로 선택된 모든 태그에 스타일을 적용하는 코드이다.

```html

<!--select_all_range.html-->
<!--왜 안되는 지 모르겠다-->

<!DOCTYPE html>
<html>
	<head>
		<title>CSS3 Selector Basic Page</title>
		<script src="http://code.jquery.com/jquery-1.11.1.js"></script>
		<script>
			/* 웹페이지가 모두 준비되면 */
			$(document).ready(function () {
			/* 모든 태그의 border 속성에 Spx solid black을 적용한다 */
			$('*').css('border', 'Spx solid black');
			});
		</script>
	</head>
	<body>
		<h1>Lorem ipsum</h1>
		<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
	</body>
</html>


```

## 태그 선택자

태그 선택자는 HTML 페이지 내부에서 특정 종류의 태그를 모두 선택할 때 사용하는 선택자이다.

| 선택자 형태 | 설명                    |
| ----------- | ----------------------- |
| 태그        | 특정한 태그를 선택한다. |
| ----------- |                         |

태그 선택자는 아래의 코드처럼 사용한다. 다음 코드는 h1 태그의 color 속성에 red 키워드를 적용하고 p 태그의 color 속성에 blue 키워드를 적용한다.

```html

<!--select_tag.html-->

<!DOCTYPE html>
<html>
	<head>
		<title>CSS3 Select Basic Page</title>
		<style>
			/* h1 태그의 color 속성에 red 키워드를 적용한다. */
			h1 { color: red; }

			/* p 태그의 color 속성에 blue 키워드를 적용한다. */
			p { color: blue; }
		</style>
	</head>
	<body>
		<h1>Lorem ipsum dolor amet</h1>
		<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
		<p>Nunc nisl turpis, aliquet et gravida non, facilisis a sem.</p>
	</body>
</html>

```

그리고 다음과 같이 여러 개의 선택자를 한꺼번에 선택해서 스타일 속성을 적용할 때는 쉼표를 사용한다.

여러 개의 태그 선택자를 쉼표로 연결해 margin 속성과 padding 속성을 적용한다.

```html

<style>
	body, p, h1, h2, h3, h4, h5, h6 { margin: 0; padding: 0; }
</style>

```

## 아이디 선택자

아이디 선택자는 특정한 id 속성을 가지고 있는 태그를 선택할 때 사용하는 선택자이다.

| 선택자 형태 | 설명 |
| ----------- | ---- |
| \#아이디            | 아이디 속성을 가지고 있는 태그를 선택한다.     |

웹 표준에 **id 속성은 웹 페이지 내부에서 중복되면 안된다**라는 규정이 있으므로 아이디 선택자는 특정한 하나의 태그를 선택할 때 사용한다.

일반적으로 아래의 코드처럼 공간 분할 태그에 id 속성을 적용하고 레이아웃을 구성한다.

```html

<!--select_id.html-->

<!DOCTYPE html>
<html>
	<head>
		<title>CSS3 Selector Basic Page</title>
		<style>
			/* id 속성값으로 header를 가지는 태그의 스타일을 지정한다. */
			#header {
				width: 800px; margin: 0 auto;
				background: red;
			}
			#wrap {
				width: 800px; margin: 0 auto;
				overflow: hidden;
			}
			#aside {
				width: 200px; float: left;
				background: blue;
			}
			#content {
				width: 600px; float: left;
				background: green;
			}
		</style>
	</head>
	<body>
		<div id="header">
			<h1>Header</h1>
		</div>
		<div id="wrap">
			<div id="aside">
				<h1>Aside</h1>
			</div>
			<div id="content">
				<h1>Content</h1>
			</div>
		</div>
	</body>
</html>

```

## 클래스 선택자

클래스 선택자는 특정한 클래스를 가지고 있는 태그를 선택할 때 사용하는 선택자이다.

| 선택자 형태 | 설명 |
| ----------- | ---- |
| .클래스      | 특정한 클래스를 가지고 있는 태그를 선택한다.     |

```html

<!--select_class.html-->

<!DOCTYPE html>
<html>
	<head>
		<title>CSS3 Selector Basic</title>
		<style>
			/* class 속성값으로 select를 가지는 태그의 color 속성에 red 키워드를 적용한다 */
			.select { color: red; }
		</style>
	</head>
	<body>
		<ul>
			<li class="select">Lorem ipsum</li>
			<li>Lorem ipsum</li>
			<li class="select">Lorem ipsum</li>
			<li>Lorem ipsum</li>
		</ul>
	</body>
</html>

```

### 여러 개의 클래스 선택자 사용

class 속성은 아래처럼 공백으로 구분해서 여러 클래스를 사용할 수 있다. 따라서 아래의 코드의 h1 태그는 .item, .header CSS 블록이 같이 적용된다.

```html

<h1 class="item header">Lorem ipsum</h1>

```

### 태그 선택자와 클래스 선택자

id 속성은 웹 페이지 내부에서 중복되지 않으므로 상관없지만 class 속성은 중복될 수 있다. 만약 class 속성이 서로 다른 태그에 사용된다면 태그 선택자와 클래스 선택자를 함께 사용해서 더 정확하게 클래스를 선택한다.

```html

<!--select_tag_class.html-->

<!DOCTYPE html>
<html>
	<head>
		<title>CSS3 Selector Basic</title>
		<style>
			/* li 태그 중 class 속성값으로 select를 가지는 태그의 color 속성을 red 키워드를 적용한다. */
			li.select { color: red; }
		</style>
	</head>
	<body>
		<h1 class="select">Lorem ipsum</h1>
		<ul>
			<li class="select">Lorem ipsum</li>
			<li>Lorem ipsum</li>
			<li>Lorem ipsum</li>
			<li>Lorem ipsum</li>
		</ul>
	</body>
</html>

```

## 속성 선택자

속성 선택자를 사용하면 특정 속성을 가진 HTML 태그를 선택할 수 있다.
속성 선택자는 지금까지 배운 다른 선택자와 함께 사용하는 선택자이다. 

속성 선택자는 기본 속성 선택자와 문자열 속성 선택자로 나눌 수 있으며 기본 속성 선택자는 많이 사용하지만 문자열 속성 선택자는 특별한 경우에만 사용한다.

### 기본 속성 선택자

기본 속성 선택자는 다음의 표와 같은 형태이다. 지금까지 배운 선택자 뒤에 대괄호([])를 사용해 속성과 값을 입력한다.

| 선택자 형태                | 설명                                                       |
| -------------------------- | ---------------------------------------------------------- |
| 선택자\[속성]              | 특정한 속성이 있는 태그를 선택한다                         |
| 선택자\[속성=값]\[속성=값] | 특정한 속성 안의 값이 특정 값과 같은 문서 객체를 선택한다. |

#### 기본 속성과 속성 선택자

input 태그는 type 속성을 입력하지 않으면 자동으로 text 속성값을 적용한다. 하지만 CSS는  HTML 태그가 기본으로 무엇을 출력하는지는 관심이 없기 때문에 코드에 명시적으로 속성값을 text라고 작성한 태그에만 스타일을 적용한다는 점에 유의하자.

### 문자열 속성 선택자

문자열 속성 선택자는 태그에 지정한 속성의 특정 문자열을 확인한다.

| 선택자 형태        | 설명                                                     |
| ------------------ | -------------------------------------------------------- |
| 선택자\[속성~=값]  | 속성 안의 값이 특정 값을 단어로 포함하는 태그를 선택한다 |
| 선택자\[속성\|=값] | 속성 안의 값이 특정 값을 단어로 포함하는 태그를 선택한다 |
| 선택자\[속성^=값]  | 속성 안의 값이 특정 값으로 시작하는 태그를 선택한다      |
| 선택자\[속성$=값]  | 속성 안의 값이 특정 값으로 끝나는 태그를 선택한다        |
| 선택자\[속성*=값]  | 속성 안의 값이 특정 값을 포함하는 태그를 선택한다        |

> 위 표를 보면 선택자\[속성~=값]과 선택자\[속성\|=값]의 설명이 같다. 하이픈(-)이 들어간 단어의 구분 방법이 다르다. 예를 들러 ko-kr 글자를 다음과 같이 인식한다.

| 선택자             | 단어 인식 |
| ------------------ | --------- |
| 선택자\[속성~=값]  | ko-kr     |
| 선택자\[속성\|=값] | ko와 kr   |

문자열 속성 선택자는 거의 사용하지 않지만 파일 형태에 따라 스타일을 적용할 때 가끔 사용한다.

```html

<!--select_string-attribute.html-->

<!DOCTYPE html>
<html>
	<head>
		<title>CSS3 Selector Basic</title>
		<style>
			/* img 태그 중에서 src 속성값이 png로 끝나는 태그의
			border 속성에 3px solid red를 적용한다 */
			img[src$=png] { border: 3px solid red; }

			/* img 태그 중에서 src 속성값이 jpg로 끝나는 태그의
			border 속성에 3px solid green를 적용한다 */
			img[src$=jpg] { border: 3px solid green; }

			/* img 태그 중에서 src 속성값이 gif로 끝나는 태그의
			border 속성에 3px solid blue를 적용한다 */
			img[src$=png] { border: 3px solid blue; }
		</style>
	</head>
	<body>
		<img src="jajq.png" width="200" height="250" />
		<img src="node.jpg" width="200" height="250" />
		<img src="ux.gif" width="200" height="250" />
	</body>
</html>

```

문자열 속성 선택자는 복잡한 CSS 프레임워크를 만들 때나 사용하는 선택자이므로, 나중에 정말 필요한 경우에만 찾아봐도 늦지 않다.

## 후손 선택자

후손 선택자는 특정한 태그 아래에 있는 후손을 선택할 때 사용하는 선택자이다.

| 선택자 형태     | 설명                                         |
| --------------- | -------------------------------------------- |
| 선택자A 선택자B | 선택자A의 후손에 위치하는 선택자B를 선택한다 |

```html

<!--select_grandchild.html-->

<!DOCTYPE html>
<html>
	<head>
		<title>CSS3 Selector Basic</title>
		<style>
			/* id 속성값으로 header를 가지는 태그의 후손 위치에 있는 h1 태그의
			   color 속성에 red 키워드를 적용한다. */
			#header h1 { color: red; }
			/* id 속성값으로 section를 가지는 태그의 후손 위치에 있는 h1 태그의
			   color 속성에 orange 키워드를 적용한다. */
			#section h1 { color: orange; }
		</style>
	</head>
	<body>
		<div id="header">
			<h1 class="title">Lorem ipsum</h1>
			<div id="nav">
				<h1>Navigation</h1>
			</div>
		</div>
		<div id="section">
			<h1 class="title">Lorem ipsum</h1>
			<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
		</div>
	</body>
</html>

```

### 후손 선택자와 관련된 주의 사항

여러 개의 선택자를 함께 사용할 때 후손 선택자를 다음과 같이 사용하는 경우가 있다.

```html

<style>
	/* id 속성값이 header인 태그의 후손 위치에 있는 h1 태그와 h2 태그의 color 속성에 red 키워드를 적용한다. */
	#header h1, h2 {color: red; }
</style>

```

위 예제의 선택자는 \#header 태그의 후손에 위치하는 h1 태그를 선택하고 일반적인 h2 태그를 선택한다.
만약 \#header 태그의 후손에 위치하는 h1 태그와 \#header 태그의 후손에 위치하는 h2 태그를 선택하고 싶다면 아래의 코드처럼 사용해야 한다.

```html

<style>
	/* id 속성값이 header인 태그의 후손 위치에 있는 h1 태그와
	   id 속성값이 header인 태그의 후손 위치에 있는 h2 태그의
	   color 속성에 red 키워드를 적용한다. */
	#header h1, #header h2 { color: red; }
<\style>

```

## 자손 선택자

자손 선택자는 특정 태그 아래에 있는 자손을 선택할 때 사용하는 선택자이다.

| 선택자 형태       | 설명 |
| ----------------- | ---- |
| 선택자A > 선택자B | 선택자A의 자손에 위치하는 선택자B를 선택한다.     |

아래의 예제는 위에서 살펴본 body 태그와 구성이 같지만 \#nav 태그 아래에 있는 h1 태그에는 스타일이 적용되지 않는다.

```html

<!--select_child.html-->

<!DOCTYPE html>
<html>
	<head>
		<title>CSS3 Selector Basic</title>
		<style>
			/* id 속성값으로 header를 가지는 태그의 후손 위치에 있는 h1 태그의
			   color 속성에 red 키워드를 적용한다. */
			#header > h1 { color: red; }
			/* id 속성값으로 section를 가지는 태그의 후손 위치에 있는 h1 태그의
			   color 속성에 orange 키워드를 적용한다. */
			#section > h1 { color: orange; }
		</style>
	</head>
	<body>
		<div id="header">
			<h1 class="title">Lorem ipsum</h1>
			<div id="nav">
				<h1>Navigation</h1>
			</div>
		</div>
		<div id="section">
			<h1 class="title">Lorem ipsum</h1>
			<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
		</div>
	</body>
</html>

```

---

참고자료

#

---