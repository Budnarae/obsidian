
---

#42Seoul #ft_transcendence

---

# 개요

==페이지 모듈은 각 페이지를 화면에 렌더링하는 기능을 지원한다.==

# 전역 상수 목록

# LoginPage

- static renderLoginPage(ftOauthUrl) : 화면에 로그인 페이지를 렌더링한다. 이 때, 버튼에 42 인증 페이지로의 링크를 부여하기 위해 42 Oauth url을 인자로 주어야 한다.
- static destroyLoginPage() : 로그인 페이지를 화면에서 지운다.

# TwoFAPage

- static renderTwoFAPage() : 화면에 2fa(google otp) 인증 페이지를 렌더링한다.
- static destroyTwoFAPage() : 2fa 인증 페이지를 화면에서 지운다.