
---

#network 

*Transmission Control Protocol*

---

[[OSI 참조 모델]]의 4계층인 전송 계층에서 사용되는 네트워크 프로토콜로, 신뢰성이 높은 데이터 통신을 보장한다. 신뢰성이 높다는 것은 데이터의 손실 없이 확실하게 상대에게 전송한다는 의미이다.

TCP는 5계층(세션 계층) 이상의 프로토콜에서 통신 데이터를 수신하여 [[패킷]]으로 분할한다. 그리고 이 패킷을 3계층(네트워크 계층)의 [[IP]]에게 전달하여 상대방에게 송신한다.

패킷을 전송하는 IP는 패킷이 순서대로 도착하는 것을 보장하지 않아, 네트워크의 혼잡 상황에 따라 패킷의 손실이나 지연에 의해 순서가 뒤바뀌는 일이 발생할 수 있다. 이에 대응하여 데이터 통신이 신뢰성을 가질 수 있도록 TCP는 다음의 방법들을 사용한다.

1. 송신 측에서 통신 데이터를 패킷으로 분할할 때 분할 순으로 시퀀스 번호를 부여한다.
2. 수신 측에서 이 번호를 확인하고 필요에 따라 순서를 정렬하여 패킷의 순서가 올바른지 확인한다.
3. 수신 측에서 수신했다는 것을 알리는 패킷(ACK 패킷)을 송신 측에 전송한다.
4. 송신 측에선 일정 시간 이상 수신 측에서 응답을 보내지 않을 경우 패킷을 재전송하여 손실을 방지한다.

---

참고자료

[그림으로 이해하는 네트워크 용어](https://product.kyobobook.co.kr/detail/S000001834837)

---