
---

#network #c #socket_programming #linux

*소켓에 인터넷 주소를 할당*

---

```c
#include <sys/socket.h>

int bind(int sockfd, struct sockaddr *myaddr, socklen_t addrlen);
```

- sockfd : 주소 정보를(IP와 PORT를) 할당할 소켓의 파일 디스크립터
- myaddr : 할당하고자 하는 주소 정보를 지니는 구조체 변수의 주소 값.
- addrlen : 두 번째 인자로 전달된 구조체 변수의 길이 정보.
+ 반환값 : 성공 시 0, 실패 시 -1 반환

특이 사항으로 [[sockaddr 구조체는 매우 사용하기 불

---

참고자료

[윤성우의 열혈 TCP/IP 소켓 프로그래밍](https://product.kyobobook.co.kr/detail/S000001589146)

---