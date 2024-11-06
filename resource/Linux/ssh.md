
---

#linux

*Secured SHell*

---

ssh는 원격으로 다른 환경에 연결하기 위한 도구이다.
본 문서는 일단 ssh에 대해 깊게 다루기보다는 기본적인 사용법만 숙지하는 것을 목표로 한다.

#### 기본적인 사용 방법

1. 연결하는 측에서는 ssh 클라이언트를 설치한다. `apt install openssh-client`
2. 연결을 지원하는 측에서는 ssh 서버를 설치한다. `apt install openssh-server`
3. 서버 측에서 /etc/ssh/sshd_config(= ssh 서버의 옵션 파일) 파일을 용도에 맞게 수정한다.

|          항목          |                  의미                   |   옵션   |
|:----------------------:|:---------------------------------------:|:--------:|
| PasswordAuthentication | 계정의 비밀번호를 사용한 인증 허용 여부 | yes / no |
|  PubkeyAuthentication  |     공개키를 사용한 인증 허용 여부      | yes / no |
|    PermitRootLogin     |     root 계정으로의 연결 허용 여부      | yes / no / **prohibit-password(공개키를 사용한 연결만 허용)**         |

4. 클라이언트 측에서 다음의 명령어를 실행한다. `ssh -p <연결에_사용할_port> <계정_id>@<서버의_ip주소>`
5. 서버 측에서 연결을 위해 계정의 비밀번호를 요구한다(Permission denied가 뜨는 경우 서버 측의 PasswordAuthentication 옵션을 확인하자).

#### 공개키를 사용한 연결

1. 클라이언트 측에서 다음의 명령어를 실행해 ssh 키 한 쌍을 생성한다. 
	- `ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
	- `-t rsa` : rsa 알고리즘으로 키를 생성
	- `-b 4096` : 4096 비트 길이의 키를 생성
	- `-C "your_email@example.com"` : 키에 대한 코멘트를 입력 (보통 이메일 주소를 입력)
2. 1의 명령어를 입력하면 다음과 같은 질문이 나온다.
	1. **파일 이름**: 기본 경로인 `~/.ssh/id_rsa`를 그대로 사용하려면 Enter 입력
	2. **패스프레이즈**: 비밀번호를 입력하여 추가 보안을 설정할 수 있음. 비밀번호 없이 진행하려면 Enter 입력
3. ssh 키 중 공개키는 서버의 ~/.ssh/authorized_keys 파일에 등록하고

---

참고자료



---