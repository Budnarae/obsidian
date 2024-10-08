
---

#network #c #socket_programming #linux

*연결 요청*

---

클라이언트는 아래의 시스템 콜을 통해 서버에 연결 요청을 송신한다.

```c
#include <sys/socket.h>

int connect(int sock, struct sockaddr *servaddr, socklen_t addrlen);
```

- sock : 클라이언트 소켓의 파일 디스크립터 전달
- servaddr : 연결요청 할 서버의 주소 정보를 담은 변수의 주소 값 전달
- addrlen : 두 번째 매개변수 servaddr에 전달된 주소의 변수 크기를 바이트 단위로 전달
+ 반환값 : 성공 시 0, 실패 시 -1 반환

클라이언트에 의해서 connect 함수가 

---

참고자료

#참고도서/윤성우의_열혈_TCP_IP_소켓_프로그래밍

---