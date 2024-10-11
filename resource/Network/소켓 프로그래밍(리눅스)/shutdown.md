
---

#network #c #socket_programming #linux

*shutdown*

---

**shutdown**은 [[Half-close]]를 구현하기 위하여 사용되는 시스템 콜로, 소켓이 보유하고 있는 두 개의 스트림 중 한 스트림만을 끊는 기능을 가지고 있다.

```c
#include <sys/socket.h>

/*
* sock : 종료할 소켓의 파일 디스크립터 전달
* howto : 종료방법에 대한 정보 전달
* 반환값 : 성공 시 0, 실패 시 -1 반환
*/
int shutdown(int sock, int howto); 
```

| 인자의 종료 |        기능        |
|:-----------:|:------------------:|
|   SHUT_RD   |  입력 스트림 종료  |
|   SHUT_WR   |  출력 스트림 종료  |
|  SHUT_RDWR  | 입출력 스트림 종료 |

shutdown의 두 번째 인자로 SHUT_RD가 전달되면 입력 스트림이 종료되어 더 이상 데이터를 수신할 수 없는 상

---

참고자료

#참고도서/윤성우의_열혈_TCP_IP_소켓_프로그래밍

---