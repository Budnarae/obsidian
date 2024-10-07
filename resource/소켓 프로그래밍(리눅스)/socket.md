
---

#network #c #socket_programming #linux

*socket*

---

```
#include <sys/socket.h>

int socket(int domain, int type, int protocol);
```

- domain : 소켓이 사용할 [[프로토콜 체계 | 프로토콜 체계(protocol family)]] 정보 전달
- type : [[ 소켓의 타입 | 소켓의 데이터 전송방식]]에 대한 정보 전달
- protocol : 두 컴퓨터 간 통신에 사용되는 프로토콜 정보 전달
+ 반환값 : 성공 시 파일 디스크립터, 실패 시 -1 반환

---

참고자료

[윤성우의 열혈 TCP/IP 소켓 프로그래밍](https://product.kyobobook.co.kr/detail/S000001589146)

---