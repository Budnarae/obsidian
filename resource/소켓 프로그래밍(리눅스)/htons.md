
---

#network #c #socket_programming #linux

*htons는 [[호스트 바이트 순서 | host network byte order]] to [[네트워크 바이트 순서 | network byte order]] - short의 약자이다.*

---

[[sockaddr_in]]에 port 번호를 저장할 때에는 [[네트워크 바이트 순서]]로 저장해야 한다. htons는 port 번호의 **바이트 순서 변환(Endian Conversions)**을 지원한다.

```C

/* 기능 : port 번호의 바이트 순서 변환
*  매개인자 : port 번호
*  반환값 : 
*/
unsigned short htons(unsigned short);

```

---

참고자료

[윤성우의 열혈 TCP/IP 소켓 프로그래밍](https://product.kyobobook.co.kr/detail/S000001589146)

---