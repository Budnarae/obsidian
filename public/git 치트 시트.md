---
tags:
  - git
---

_git cheet sheet_

---

**git에서 잦은 빈도로 사용되는 명령어와 관련된 개념들을 요약하는 문서입니다.**

[여기](https://git-scm.com/book/ko/v2)를 참고하여 만들었습니다.

실용적인 정보를 중심으로 정리하며 git을 사용하는 데 필요없거나(ex. git과 다른 버전 관리 시스템의 차이) 낮은 빈도로 사용되는 기능들은 생략합니다.

# git config

**git 설정**에 대한 보다 자세한 설명은 [여기](https://git-scm.com/book/ko/v2/%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0-Git-%EC%B5%9C%EC%B4%88-%EC%84%A4%EC%A0%95)로

==사용자 이름과 이메일 주소 설정==

이 명령어는 git 설치 후 무조건 1회는 실행해야 한다.

```bash

git config --global user.name "John Doe"
git config --global user.email "johndoe@example.com"

```

==git이 사용할 편집기 설정==

```bash

git config --global core.ditor emacs

```

==설정 확인==

```bash

git config --list

```

==특정 키값만 확인==

```bash

git config <key

```