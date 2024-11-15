
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

# 스키마 schema의 사용

 <iframe width="640" height="360" src="https://www.youtube.com/embed/9stHa3mRbNI" title="DATABASE2 MySQL - 6. 스키마의 사용" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>



---

참고자료

#참고링크/생활코딩 

---