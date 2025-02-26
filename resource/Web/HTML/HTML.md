
---

#web #network #language/html

*hyper text markup language*

---

# 현재의 HTML 표준과 그 특성

현재의 HTML 표준은 **HTML5**이다. HTML5는 이전 표준과 비교하였을 때 아래와 같은 차별점을 가지고 있다.

## 멀티미디어

동영상이나 음악을 재생할 수 있다.

## 그래픽

하드웨어의 가속을 받아 2차원 그래픽과 3차원 그래픽을 구현할 수 있다.

2차원 그래픽의 구현을 위해 아래의 방법을 사용할 수 있다.

1. SVG 태그를 이용한 2차원 벡터 그래픽 구현
2. 자바스크립트 캔버스를 사용한 2차원 래스터 그래픽 구현

3차원 그래픽을 구현하는 방법은 아래와 같다.

1. CSS3를 사용한 3차원 구현
2. 자바스크립트 WebGL을 사용한 3차원 구현

## 통신

서버와 소켓 통신을 할 수 있다.

## 장치 접근

장치에 접근하여 장치의 정보와 기능을 사용할 수 있다.
예를 들어 스마트폰의 배터리 잔량과 같은 정보를 가져오거나 진동벨을 울릴 수 있다.

## 오프라인 및 저장소

인터넷에 연결되지 않은 상태에서도 애플리케이션이 동작할 수 있다.

## HTML5 시멘틱 태그

시멘틱 태그를 제공한다.

시멘틱 태그는 시멘틱 웹의 구현을 위해 존재한다.
시멘틱 웹이란 검색 엔진 같은 프로그램이 정보의 의미를 분석하고 자료를 검색 및 처리하여 제공하는 지능형 웹을 의미한다.

> 시멘틱 Sementic은 사전적으로 '의미론적인'이라는 뜻이다.

## CSS3 스타일시트

CSS3 스타일 시트를 완벽하게 지원한다. CSS3 스타일시트를 통해 3차원 변환은 물론 애니메이션 효과를 적용할 수 있다.

## 성능 및 통합

추가 기능을 사용하여 웹의 성능을 극대화할 수 있다. 예를 들어 웹 워커를 사용하면 사용자의 화면이 멈추는 일 없이 연산을 처리할 수 있다.

# HTML5 기본 용어 정리

HTML 5를 공부하려면 기본적으로 [[HTML 태그, 요소 그리고 속성]]이라는 용어를 알아야한다.

# 주석

HTML 페이지는 다음과 같은 방법을 사용해 주석을 입력한다.

```html

<!-- 주석 -->

```

# HTML5 페이지 구조

이제부터 HTML 페이지의 기본적인 구조를 알아보자. 모든 HTML5 페이지는 다음 코드에서 시작한다.

```html

<!DOCTYPE html>
<html>
<head>
	<title>HTML5 Basic Page</title>
</head>
<body>

</body>
</html>

```

---

참고자료

#참고도서/모던_웹_디자인을_위한_HTML5_CSS3_입문 

---