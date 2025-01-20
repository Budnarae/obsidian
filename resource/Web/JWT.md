
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

JWT 토큰은 누군가에게 갈취당하더라도 아무나 해독하지 못하도록 base64라는 방식

---

참고자료

#참고링크/생활코딩 

---