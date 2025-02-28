
---

그동안 수행했던 개발자 교육과정 **42 서울**의 공통 과정 과제들을  정리한 저장소입니다.

---

# Libft

_C 언어 기초_

strlcpy, strlcat 같은 c 라이브러리의 함수들을 직접 구현해보는 과제

# get_next_line

_파일 입출력 기초_

다음의 기능과 형식을 가진 `get_next_line`이라는 함수 만들기

```c

// 입력값 : 파일 디스크립터
// 반환값 : 파일로부터 문장 하나를 추출하여 반환
char *get_next_line(int fd);

```

첫번째로 get_next_line을 호출하면 파일의 첫번째 문장, 두번째로 get_next_line을 호출하면 파일의 두번째 문장, n번째로 get_next_line을 호출하면 파일의 n번째 문장을 호출함.
