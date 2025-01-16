
---

#language/JavaScript #web

*JavaScript Object Notation*

---

# JSON이란?

**JSON**은 클라이언트와 서버 간의 HTTP 통신을 위한 텍스트 데이터 포맷이다. 자바스크립트에 종속되지 않는 언어 독립형 데이터 포맷으로, 대부분의 프로그래밍 언어에서 사용할 수 있다.

# JSON 표기 방식

JSON은 자바스크립트의 객체 리터럴과 유사하게 키와 값으로 구성된 순수한 텍스트다.


```javascript

{
	"name": "Lee",
	"age": 20,
	"alive": true,
	"hobby": ["traveling", "tennis"]
}

```

==JSON의 키는 반드시 큰따옴표로 묶어야 한다.== 값은 객체 리터럴과 같은 표기법을 그대로 사용할 수 있다. 하지만 문자열은 반드시 큰따옴표로 묶어야 한다.

# JSON.stringify

**JSON.stringify** 메서드는 객체를 JSON 포맷의 문자열로 변환한다. 클라이언트가 서버로 객체를 전송하려면 객체를 문자열화해야 하는데 이를 직렬화 Serializing이라 한다.

---

참고자료

#참고도서/모던_자바스크립트_Deep_Dive 

---