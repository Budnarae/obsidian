
---

그동안 수행했던 개발자 교육과정 **42 서울**의 공통 과정 과제들을  정리한 저장소입니다.

---

# Libft

_C 언어 기초_

strlcpy, strlcat 같은 c 라이브러리의 함수들을 직접 구현해보는 과제

# get_next_line

_파일 입출력, static 변수_

다음의 기능과 형식을 가진 `get_next_line`이라는 함수를 만드는 과제

```c

// 입력값 : 파일 디스크립터
// 반환값 : 파일로부터 문장 하나를 추출하여 반환.
// n번째로 get_next_line을 호출하면 파일의 n번째 문장을 반환한다.
char *get_next_line(int fd);

```

`/42_innercircle_course/get_next_line/` 경로의 `tester.c` 파일을 참조하여 tester 파일을 실행시키면 `get_next_line`의 동작을 확인할 수 있다.

# ft_printf

_가변 인자_

c 라이브러리의 `printf`의 기능을 제한적으로 구현하는 과제

`/42_innercircle_course/ft_printf/` 경로의 `tester.c` 파일을 참조하여 tester 파일을 실행시키면 `ft_printf`의 동작을 확인할 수 있다.

# Born2beroot

_가상 머신, 리눅스 기초_

VirtualBox를 사용하여 linux 가상 환경을 띄운 후, 그 환경에서 여러 서비스들을 설정하는 과제

# pipex

_멀티 프로세싱_

쉘의 **파이프** 기능을 구현해보는 과제


# push_swap

_자료구조, 알고리즘_

두 개의 스택을 사용하여 뒤섞인 숫자 배열을 정렬하는 과제
이 과제에서 제시하는 스택은 일반적인 스택과 달리 추가적인 동작들을 적용할 수 있다.

# FdF

_그래픽스 기초_