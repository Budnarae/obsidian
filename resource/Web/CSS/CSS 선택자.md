
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

---

참고자료

#

---