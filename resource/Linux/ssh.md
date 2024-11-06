
---

#linux

*Secured SHell*

---

ssh는 원격으로 다른 환경에 연결하기 위한 도구이다.
본 문서는 일단 ssh에 대해 깊게 다루기보다는 기본적인 사용법만 숙지하는 것을 목표로 한다.

#### 사용 방법

1. 연결하는 측에서는 ssh 클라이언트를 설치한다. `apt install openssh-client`
2. 연결을 지원하는 측에서는 ssh 서버를 설치한다. `apt install openssh-server`
3. 서버 측에서는 /etc/ssh/sshd_config 파일을 용도에 맞게 수정한다.

|               항목                |                  의미                   |   옵션   |
|:---------------------------------:|:---------------------------------------:|:--------:|
|      PasswordAuthentication       | 계정의 비밀번호를 사용한 인증 허용 여부 | yes / no |
|       PubkeyAuthentication        |     공개키를 사용한 인증 허용 여부      | yes / no |
| PermitRootLogin prohibit-password |                                         |          |

---

참고자료



---