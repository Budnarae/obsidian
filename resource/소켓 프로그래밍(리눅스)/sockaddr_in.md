
---

#network #c #socket_programming #linux

*주소 정보의 표현*

---

sockaddr_in  구조체는 아래의 형태를 가지며, bind() 함수에 주소 정보를 전달하는 용도로 사용된다.

```C
struct sockaddr_in
{
	sa_family_t    sin_family;
	uint16_t       sin_port;
	struct in_addr sin_addr;
	char.          sin_zero[8];
}
```

|   member   |      type      |  typedef  |                                의미                                |    예시     |
|:----------:|:--------------:|:---------:|:------------------------------------------------------------------:|:-----------:|
| sin_family |  sa_family_t   | uint8_t |                      주소체계(address Family)                      |   PF_INET   |
|  sin_port  |    uint16_t    |           |                      16비트 TCP/UDP PORT 번호                      | htons(port) |
|  sin_addr  | struct in_addr |           |                           32비트 IP 주소                           |    후술     |
|  sin_zero  |    char[8]     |           | 실질적인 의미가 없으며 구조체의 크기를 특정크기로 맞추기 위해 사용 |             |

uint8_t와 같은 **POSIX(Portable Operating System Interpace)** 자료형을 사용하는 이유는 어떠한 경우에도 1 바이트 자료형임을 보장받기 위해서이다.

#### sin_family

**sin_family**에는 프로토콜이 사용하는 주소체게

---

참고자료

[윤성우의 열혈 TCP/IP 소켓 프로그래밍](https://product.kyobobook.co.kr/detail/S000001589146)

---