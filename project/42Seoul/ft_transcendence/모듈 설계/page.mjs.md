
---

#42Seoul #ft_transcendence

---

# 개요

==페이지 모듈은 각 페이지를 화면에 렌더하는 기능을 지원한다.==

==FtOauth 클래스는 42 oauth 인증에 관련된 기능을 지원한다.==
==TwoFactorOauth 클래스는 2fa 인증에 관련된 기능을 지원한다.==

# 전역 상수 목록

- clientId : 42 api의 클라이언트 id
- redirectUri : 42 api에서 콜백할 uri
- authUrl : 42 oauth 페이지로 넘어가기 위한 최종 url

# FtOauth

- static isAlreadyAuth(url) : 현재 url에 code가 포함되어 있으면 code를, 그렇지 않으면 undefined를 반환한다.
- static getFtOauthUrl : 42 인증 페이지로의 url을 반환한다.