
---

#database

*MySQL의 my는 개발자의 딸의 이름에서 유래한 것이다.*

---

==들어가기에 앞서==

본 문서는 42 seoul의 프로젝트 inception의 해결을 위해 작성되었습니다. inception은 **MariaDB** 지식을 요구하고 아래에서 제시되는 자료들은 모두 **MySQL**을 기준으로 하나 MySQL의 커맨드는 대부분이 **MaraiDB**에서 호환되기 때문에 문제가 없다고 생각하여 첨부합니다.

---

# Intro

<iframe width="640" height="360" src="https://www.youtube.com/embed/h_XDmyz--0w" title="DATABASE2 MySQL - 1.수업소개" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

[[데이터베이스]] 문서 참고.
현 데이터베이스의 가장 보편적인 형식은 **관계형 데이터베이스**이며 데이터를 **표의 형태로 관리**하여 **정렬, 검색, 표시 및 숨김 그 외에도 많은 기능**들을 편리하게 사용할 수 있다.

MySQL의 가장 큰 장점은 무료이면서 관계형 데이터베이스의 핵심 기능들을 포함하고 있다는 것이다. **웹**이 폭발적으로 성장하면서 웹 개발자들에게 선택받은 MySQL은 많은 수요를 확보하였다.

# 데이터베이스의 목적

<iframe width="640" height="360" src="https://www.youtube.com/embed/l3jMQh-NqLY" title="DATABASE2 MySQL - 2.데이터베이스의 목적" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

MySQL은 **SQL**이라는 언어를 사용해서 데이터를 조작할 수 있다.

# MySQL 설치

[다음 참고](https://opentutorials.org/course/3161/19532)

# MySQL의 구조

<iframe width="640" height="360" src="https://www.youtube.com/embed/IWEa4DN_1Yk" title="DATABASE2 MySQL - 4.MySQL의 구조" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

MySQL은 3가지 구성요소로 되어 있다.

1. 표 table : 정보가 저장되는 장소
2. 데이터베이스 database 또는 스키마 schema: 여러 개의 표들을 묶어 관리하는 단위
3. 데이터베이스 서버 database server : 여러 개의 스키마를 묶어 관리하는 단위

# MySQL 서버 접속

<iframe width="640" height="360" src="https://www.youtube.com/embed/bzhFcbin8_g" title="DATABASE2 MySQL - 5.서버접속" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

데이터베이스의 효용

- 보안성이 좋다.
	1. 자체적인 보안 체계를 가지고 있다.
	2. 사용자 권한 설정을 할 수 있다.

다음의 커맨드를 이용하여 서버에 접속한다.

`./mysql -uroot -p`

| 옵션 | 용도                                |
| ---- | ----------------------------------- |
| `-u` | 어느 유저로 서버에 접속할 지를 지정 |
| `-p` | 계정의 비밀번호 입력                |

다음의 커맨드를 사용하여 서버와의 연결을 끊는다.

`exit`

# 스키마 schema의 사용

 <iframe width="640" height="360" src="https://www.youtube.com/embed/9stHa3mRbNI" title="DATABASE2 MySQL - 6. 스키마의 사용" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

다음의 명령어를 사용하여 새로운 스키마를 만든다.

`CREATE DATABASE <만들고자 하는 스키마의 이름>;`

다음의 명령어를 사용하여 기존의 스키마를 삭제한다.

`DROP DATABASE <제거하고자 하는 스키마의 이름>;`

다음의 명령어를 사용하여 현재 있는 스키마들의 목록을 출력한다.

`SHOW DATABASES;`

다음의 명령어를 사용하여 MySQL에게 지금부터 작업할 스키마를 통지한다.

`USE <작업하고자 하는 스키마의 이름>;`

# SQL과 테이블 구조

<iframe width="640" height="360" src="https://www.youtube.com/embed/9stHa3mRbNI" title="DATABASE2 MySQL - 6. 스키마의 사용" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

**SQL**은 **Structured Query Language**의 약자이다. 여기서 **Query**는 **요청하다, 질의하다**라는 뜻이다.

표 table은 열 colume과 행 row으로 이루어져 있다.

# MySQL 테이블의 생성

<iframe width="640" height="360" src="https://www.youtube.com/embed/d3ye07XRexs" title="DATABASE2 MySQL - 8.1.테이블의 생성" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

<iframe width="640" height="360" src="https://www.youtube.com/embed/fPULu-Q-OlQ" title="DATABASE2 MySQL - 8.2테이블의 생성" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

`;`을 붙이고 줄바꿈하면 해당 line이 실행되지만 그냥 줄바꿈하면 line이 실행되지 않고 계속 입력을 받는다 -> 긴 line을 입력할 때 줄바꿈을 해가며 가독성 좋게 입력할 수 있다.

다음의 커맨드를 사용하여 새로운 열을 만든다.

```sql
CREATE TABLE topic(
	<topic의 이름> <topic의 data type>(<얼만큼의 길이만큼 저장할 수 있는가>) <필드 공백의 허용 여부>
);
```

==topic의 data type==
[다음 참고](https://incodom.kr/DB_-_%EB%8D%B0%EC%9D%B4%ED%84%B0_%ED%83%80%EC%9E%85/MYSQL)

==필드 공백의 허용 여부란 무엇인가==
해당 열(topic)에 무조건 값이 들어가야 하는지, 아니면 비어있을 수 있는지를 설정하는 영역이다.

- NOT NULL : 무조건 값을 대입하여야 한다.
- NULL : 비어있는 채로 둘 수 있다.

==AUTO_INCREMENT==
특정 열의 값을 위의 행의 공간 + 1로 자동으로 대입해주는 옵션

다음은 실행 가능한 구체적인 예이다.

```sql
CREATE TABLE topic(
	id INT(11) NOT NULL AUTO_INCREMENT,
	title VARCHAR(100) NOT NULL,
	description TEXT NULL,
	created DATETIME NOT NULL,
	author VARCHAR(30) NULL,
	profile VARCHAR(100) NULL,
	PRIMARY KEY(id)
);
```

==PRIMARY KEY(<topic의 이름>)==

- 해당 열(topic)에서는 중복을 허용하지 않는다는 의미

==ERROR1820 (HY000)==

MySQL에 처음 접속하면 기본적으로 유저마다 비밀번호를 자동으로 할당해주는데, 이 비밀번호를 갱신하지 않고 작업을 시도하면 `ERROR1820 (HY000)`을 맞게 된다.

아래의 커맨드를 사용하여 비밀번호를 갱신하여 해결할 수 있다.

`SET PASSWORD = PASSWORD('<갱신하고자 하는 새로운 비밀번호>')`

---

MySQL은 사용자로 하여금 **정해진 포맷**대로 데이터를 저장하도록 강제할 수 있다.

# MySQL의 CRUD

<iframe width="640" height="360" src="https://www.youtube.com/embed/0pU6_5BQ2Dk" title="DATABASE2 MySQL - 9.CRUD" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

# SQL의 INSERT 구문

<iframe width="1270" height="1440" src="https://www.youtube.com/embed/75LHpeOQiOs" title="DATABASE2 MySQL - 10.INSERT" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

다음의 명령어를 통해 테이블의 구조를 볼 수 있다.

`DESC topic;`

다음의 명령어를 통해 표에 값을 삽입할 수 있다.

`INSERT INTO <삽입하고자하는 table 이름>`

---

참고자료

#참고링크/생활코딩 

---