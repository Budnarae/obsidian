
---

#language/JavaScript #web 

__

---

# XMLHttpRequest

브라우저는 주소창이나 HTML의 form 태그 또는 a 태그를 통해 HTTP 요청 전송 기능을 기본 제공한다. 자바스크립트를 사용하여 HTTP 요청을 전송하려면 XMLHTTPRequest 객체를 사용한다. Web API인 XMLHttpRequest 객체는 HTTP 요청 전송과 HTTP 응답 수신을 위한 다양한 메서드와 프로퍼티를 제공한다.

## XMLHttpRequest 객체 생성

XMLHttpRequest 객체는 XMLHttpRequest 생성자 함수를 호출하여 생성한다. XMLHttpRequest 객체는 브라우저에서 제공하는 Web API이므로 브라우저 환경에서만 정상적으로 실행된다.

```javascript

// XMLHttpRequest 객체의 생성
const xhr = new XMLHttpRequest();

```

## XMLHTTPRequest 객체의 프로퍼티와 메서드

XMLHttpRequest 객체는 다양한 프로퍼티와 메서드를 제공한다. 대표적인 프로퍼티와 메서드는 다음과 같다. 중요한 프로퍼티와 메서드는 볼드체로 표시했다.

### XMLHttpRequest 객체의 프로토타입 프로퍼티

#### readyState

HTTP 요청의 현재 상태를 나타내는 정수. 다음과 같은 XMLHttpRequest의 정적 프로퍼티를 값으로 갖는다.

- UNSENT: 0
- OPENED: 1
- HEADERS_RECEIVED: 2
- LOADING: 3
- DONE: 4

#### status

HTTP 요청에 대한 응답 상태(HTTP 상태 코드)를 나타내는 정수
ex) 200

#### statusText

HTTP 요청에 대한 응답 메시지를 나타내는 문자열
ex) "OK"

#### responseType

HTTP 응답 타입
ex) document, json, text, blob, arraybuffer

#### response

HTTP 요청에 대한 응답 몸체 reponse body. reponseType에 따라 타입이 다르다.

#### reponseText

서버가 전송한 HTTP 요청에 대한 응답 문자열

### XMLHttpRequest 객체의 이벤트 핸들러 프로퍼티
### XMLHttpRequest 객체의 메서드
### XMLHttpRequest 객체의 정적 프로퍼티

(추후 보충)

## HTTP 요청 전송

HTTP 요청을 전송하는 경우 다음 순서를 따른다.

1. XMLHttpRequest.prototype.open 메서드로 HTTP 요청을 초기화한다.
2. 필요에 따라 XMLHttpRequest.prototype.setRequestHeader 메서드로 특정 HTTP 요청의 헤더 값을 설정한다.
3. XMLHttpRequest.prototype.send 메서드로 HTTP 요청을 전송한다.

```javascript

// XMLHttpRequest 객체 생성
const xhr = new XMLHttpRequest();

// HTTP 요청 초기화
xhr.open('GET', '/users');

// HTTP 요청 헤더 설정
// 클라이언트가 서버로 전송할 데이터의 MIME 타입 지정: json
xhr.setRequestHeader('content-type', 'application/json');

// HTTP 요청 전송
xhr.send();

```

###

---

참고자료

#참고도서/모던_자바스크립트_Deep_Dive 

---