
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

| member     | type           | typedef   | 의미                     | 예시        |
| ---------- | -------------- | --------- | ------------------------ | ----------- |
| sin_family | sa_family_t    | __uint8_t | 주소체계(address Family) | PF_INET     |
| sin_port   | uint16_t       |           | 16비트 TCP/UDP PORT 번호 | htons(port) |
| sin_addr   | struct in_addr |           | 32비트 IP 주소           | 후술        |
| sin_zero   | char[8]        |           | 실질적                         |             |

---

참고자료

[윤성우의 열혈 TCP/IP 소켓 프로그래밍](https://product.kyobobook.co.kr/detail/S000001589146)

---