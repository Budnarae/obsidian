
---

#network #c #socket_programming #linux

*inet_addr*

---

[[sockaddr_in#^d7a9de | sockaddr_in]]의 멤버 sin_addr에는 32비트 정수형으로 ip 주소를 저장해야 한다.  **inet_addr**은 **aaa.bbb.ccc.ddd** 꼴의 문자열로 표현된 ip 주소를  32비트 정수로 변환하는 번거로운 작업을 수행한다. 또한, 변환 과정에서 [[네트워크 바이트 순서]]로의 변환도 동시에 지원한다.

```C
#include <arpa/inet.h>

/* 입력값 : 문자열로 표현된 ip 주소
*  반환값 : 성공 시 빅엔디안으로 변환된 32비트 정수 값, 실해 시 INADDR_NONE 반환
*/
in_addr_t inet_addr(const char *string);
```

비슷한 기능을 수행하는 함수로 [[inet_aton]]이 있다.
만약 네트워크 바이 32비트 정수

---

참고자료

[윤성우의 열혈 TCP/IP 소켓 프로그래밍](https://product.kyobobook.co.kr/detail/S000001589146)

---