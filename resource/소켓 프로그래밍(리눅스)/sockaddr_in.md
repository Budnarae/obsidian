
---

#network #c #socket_programming #linux

*주소 정보의 표현*

---

sockaddr_in  구조체는 아래의 형태를 가지며, bind() 함수에 주소 정보를 전달하는 용도로 사용된다.

```C
struct sockaddr_in
{
	sa_family_t sin_family;
	uint16_t    sin_port;
	struct in_addr sin_addr;
	char.       sin-zero[8];
}
```

| member     | type        | typedef | 기능 | 
| ---------- | ----------- | ------- | ---- |
| sin_family | sa_family_t |         |      |

---

참고자료

[윤성우의 열혈 TCP/IP 소켓 프로그래밍](https://product.kyobobook.co.kr/detail/S000001589146)

---