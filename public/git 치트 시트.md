---
tags:
  - git
---

_git cheet sheet_

---

**git에서 잦은 빈도로 사용되는 명령어와 관련된 개념들을 요약하는 문서입니다.**

[여기](https://git-scm.com/book/ko/v2)를 참고하여 만들었습니다.

실용적인 정보를 중심으로 정리하며 git을 사용하는 데 필요없거나(ex. git과 다른 버전 관리 시스템의 차이) 낮은 빈도로 사용되는 기능들은 생략합니다.

# git config - 설정

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

```text

git config <key>

```

```bash

$ git config user.name
John Doe

```

키값이 세 개의 설정 파일 중 어떤 것에서 설정된 것인지 알기 위해선 --show-origin 옵션과 사용한다.

```bash

$ git config --show-origin rerere.autoUpdate
file:/home/johndoe/.gitconfig	false

```

# git help - 도움말



명령어에 대한 도움말이 필요할 때 도움말을 보는 방법은 두 가지로 동일한 결과를 볼 수 있다.

```bash

$ git help <verb>
$ man git-<verb>

```

예를 들어 아래와 같이 실행하면 `git config` 명령에 대한 도움말을 볼 수 있다.

```bash

$ git help config

```

Git 명령을 사용하기 위해 매우 자세한 도움말 전체를 볼 필요 없이 각 명령에서 사용할 수 있는 옵션들에 대해서 간략히 살펴볼수도 있다. `-h`, `--help` 옵션을 사용하면 다음과 같이 Git 명령에서 사용할 수 있는 옵션들에 대한 간단한 도움말을 출력한다.

```bash

$ git add -h
usage: git add [<options>] [--] <pathspec>...

    -n, --dry-run         dry run
    -v, --verbose         be verbose

    -i, --interactive     interactive picking
    -p, --patch           select hunks interactively
    -e, --edit            edit current diff and apply
    -f, --force           allow adding otherwise ignored files
    -u, --update          update tracked files
    -N, --intent-to-add   record only the fact that the path will be added later
    -A, --all             add changes from all tracked and untracked files
    --ignore-removal      ignore paths removed in the working tree (same as --no-all)
    --refresh             don't add, only refresh the index
    --ignore-errors       just skip files which cannot be added because of errors
    --ignore-missing      check if - even missing - files are ignored in dry run
    --chmod <(+/-)x>      override the executable bit of the listed files

```

# 저장소 관련

==이미 존재하는 디렉토리를 저장소로 만들기==

```bash

git init

```

==파일의 변경을 staged 상태로 만듬==

```bash

git add <file_name>

```

==파일의 변경을 commited 상태로 만듬==

```bash

git commit -m "<commit_name>"

```

==기존 저장소 Clone==

```bash

git clone <repository_url>

```

다른 디렉토리 이름으로 클론하려면

```bash

git clone <repository_url> <other_name>

```

==파일 상태 확인==

```bash

git status

```