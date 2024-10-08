
---

#network #c #socket_programming #linux

*자기 자신의 IP 주소를 나타내는 상수*

---

자기 자신의 IP 주소를 나타내는 32비트 정수형 상수이다. 서버 프로그램의 경우 이 상수를 사용하면 별도의 IP 주소를 입력하지 않아도 되서 편리하다. 주로 [[htons#^84391e | htonl]]을 사용하여 [[네트워크 바이트 순서]]로 변환한 후 [[sockaddr_in#^d7a9de | sockaddr_in의 sin_addr]]로 전달하는데 사용한다.

```C
struct sockaddr_in addr;
addr.sin_addr.s_addr = htonl(INADDR_ANY);
```

> #### 서버 소켓 생성시 IP 주소가 필요한 이유
> 서버 소켓은 생성 시 자신이 속한 컴퓨터의 IP 주소로 초기화가 이뤄

---

참고자료

[윤성우의 열혈 TCP/IP 소켓 프로그래밍](https://product.kyobobook.co.kr/detail/S000001589146)

---