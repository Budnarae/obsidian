
---

#security #cryptograph #web

_Json Web Token_

---

<iframe width="787" height="443" src="https://www.youtube.com/embed/36lpDzQzVXs" title="JWT" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**JWT**는 Json Web Token의 약자이다. 자료를 [[JSON]] 형태로 다른 장치에게 안전하게 전송하기 위한 프로토콜이다.

JWT는 다음의 세 가지 요소로 이루어져 있다.

1. 헤더 header : "alg"(알고리즘의 약자)와 "typ"이라는 두 개의 프로퍼티로 구성되어있다. alg 프로퍼티에는 서명을 어떠한 알고리즘으로 암호화했는지를 저장한다.
2. 페이로드 payload : 실질적인 내용을 저장하는 부분이다. payload의 각 부분을 claim(주장)이라고 하는데, 이는 받는 입장에서 payload의 내용을 완전히 신뢰할 수 없기 때문이다.
3. 서명 signature : 페이로드의 내용을 보증하는 보안적 요소

JWT 토큰은 누군가에게 갈취당하더라도 아무나 해독하지 못하도록 base64라는 방식으로 암호화되어 전송된다.

JWT는 다음과 같은 방식으로 사용된다.

1. JWT 토큰을 작성하여 보내는 측은(예를 들어, 웹 서버라고 하자) 본문(페이로드)를 작성한 후 특정한 암호화 알고리즘과(HMAC을 썼다고 가정하자) private 키를 사용하여 본문을 암호화하여 서명을 작성한다. HMAC 알고리즘을 사용하였으므로 토큰의 헤더 부분이 HMAC 알고리즘이 사용되었음이 기록된다.
2. JWT 토큰을 받은 프론트 측은 긴 시간이 지난 후 웹 서버에게 자신을 인증하기 위해 해당 토큰을 다시 웹 서버에게 보낸다.
3. 토큰의 헤더의 HMAC 알고리즘이 저장되어 있으므로 웹 서버는 HMAC 알고리즘을 불러와 가지고 있는 private 키와 토큰의 페이로드를 사용하여 새로운 서명을 만든다.
4. 새로 만든 서명이 토큰의 서명과 일치한다면 서버는 토큰이 자신이 발행한 것이라고 확신할 수 있다.

# JWT의 활용

1. 인증
2. 정보 공유
3. 

---

참고자료

#참고링크/생활코딩 

---