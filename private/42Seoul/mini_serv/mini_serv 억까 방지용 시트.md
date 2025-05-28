		
---

#42Seoul #network #server #socket_programming 

*micro_serv*

---

Assignment name  : mini_serv
과제 이름 : mini_serv

Expected files   : mini_serv.c
제출할 파일 : mini_serv.c

Allowed functions: write, close, select, socket, accept, listen, send, recv, bind, strstr, malloc, realloc, free, calloc, bzero, atoi, sprintf, strlen, exit, strcpy, strcat, memset
허용 함수는 위와 같습니다.

---

Write a program that will listen for client to connect on a certain port on 127.0.0.1 and will let clients to speak with each other.
클라이언트들로 하여금 127.0.0.1 주소의 특정한 포트로 연결하여 서로 소통할 수 있게끔하는 프로그램을 만드세요.

This program will take as first argument the port to bind to.
이 프로그램은 첫 번째 인자로 bind에 사용할 포트를 받습니다.

If no argument is given, it should write in stderr "Wrong number of arguments" followed by a \n and exit with status 1.
만약에 아무런 인자도 주어지지 않는다면, 표준 에러로 "Wrong number of arguments"에 개행(\n)을 붙여 출력하고 exit status 1로 종료되어야 합니다.

If a System Calls returns an error before the program start accepting connection, it should write in stderr "Fatal error" followed by a \n and exit with status 1.
만약에 시스템 콜이 연결이 완료되기 전에(accepting connection) 오류를 반환한다면, 표준 에러로 "Fatal error"에 개행(\n)을 붙여 출력하고 exit status 1로 종료되어야 합니다.

If you can't allocate memory it should write in stderr "Fatal error" followed by a \n and exit with status 1
만약에 당신이 메모리를 할당할 수 없다면 표준 오류로 "Fatal error"에 개행(\n)을 붙여 출력하고 exit status 1로 종료되어야 합니다.

Your program must be non-blocking but client can be lazy and if they don't read your message you must NOT disconnect them...
당신의 프로그램은 non-block으로 실행되어야 합니다. 하지만 클라이언트는 게으를 수 있으니 그들이 당신의 메시지를 읽지 않는다고 해서 연결을 끊어서는 안됩니다.

Your program must not contains \#define preproc
당신의 프로그램은 \#define preproc을 포함해선 안됩니다.

Your program must only listen to 127.0.0.1.
당신의 프로그램은 오직 127.0.0.1 주소로만 수신해야 합니다.

The fd that you will receive will already be set to make 'recv' or 'send' to block if select hasn't be called before calling them, but will not block otherwise. 
당신에게 주어지는 파일 디스크립터(fd)는 recv 또는 send를 위해 쓰일 것이고, select를 앞선 함수들을 호출하기 전에 호출하면 block을 방지할 수 있습니다.
	
When a client connect to the server:
- the client will be given an id. the first client will receive the id 0 and each new client will received the last client id + 1
- %d will be replace by this number
- a message is sent to all the client that was connected to the server: "server: client %d just arrived\n"
클라이언트가 서버에 연결할 때:
- 클라이언트는 id를 부여받습니다. 첫번째 클라이언트는 id 0을 부여받고 새로운 클라이언트는 그 직전 클라이언트의 id + 1을 id로 부여받습니다.
- %d는 이 id로 대체되어야 합니다.
- 서버에 접속해 있던 모든 클라이언트에게 다음의 메세지를 보냅니다: "server: client %d just arrived\n"

clients must be able to send messages to your program.
- message will only be printable characters, no need to check
- a single message can contains multiple \n
- when the server receive a message, it must resend it to all the other client with "client %d: " before every line!

클라이언트는 당신의 프로그램에 메시지를 전송할 수 있어야 합니다.
- 메시지는 출력 가능한(printable) 캐릭터로만 구성되며, 이를 체크할 필요는 없습니다(예외 처리할 필요 없다는 뜻).
- 하나의 메시지는 여러 개의 개행(\n)을 포함할 수 있습니다.
- 서버가 메시지를 수신할 때, 다른 모든 클라이언트에게 "client %d: "를 접두사로 붙여 해당 메시지를 broadcast해야 합니다.

When a client disconnect from the server:
- a message is sent to all the client that was connected to the server: "server: client %d just left\n"

클라이언트가 서버와의 연결을 끊을 때:
- 서버에 연결되어 있는 모든 클라이언트에게 다음의 메시지를 보내야 합니다: "server: client %d just left\n"

Memory or fd leaks are forbidden
메모리나 fd의 누수는 용납되지 않습니다.

To help you, you will find the file main.c with the beginning of a server and maybe some useful functions. (Beware this file use forbidden functions or write things that must not be there in your final program)
당신을 돕기위해서, 우리는 서버의 기초와 몇몇 유용한 함수를 포함하고 있는 main.c 파일을 준비했습니다(이 파일이 당신의 최종 프로그램에 포함되어서는 안될 금지 함수와 출력을 포함하고 있다는 사실에 유의하세요).

Warning our tester is expecting that you send the messages as fast as you can. Don't do un-necessary buffer.
저희의 테스터기는 당신의 프로그램이 가능한 한 빠르게 메시지를 전송할 것을 가정한다는 사실에 유의하세요. 불필요하게 프로그램을 지연시키지 마세요.

Evaluation can be a bit longer than usual...
평가는 평소보다 좀 더 오래 걸릴 수 있습니다...

Hint: you can use nc to test your program
힌트: 당신은 테스트를 위해서 nc를 사용할 수 있습니다.

Hint: you should use nc to test your program
힌트: 당신은 테스트를 위해서 nc를 사용해야만 합니다.

Hint: To test you can use fcntl(fd, F_SETFL, O_NONBLOCK) but use select and NEVER check EAGAIN (man 2 send)
	힌트: 테스트를 위해서 당신은 fcntl(fd, F_SETFL, O_NONBLOCK)을 사용할 수 있지만 select를 사용하여야 하며 절대 EAGAIN 옵션을 체크해서는 안됩니다.

---

# 숨겨진 조건에 관하여

## 구분자

이상이 exam 06 mini_serv의 subject 원본이다. 언뜻 보면 일반적인 echo 서버에 접두사(client : %d)를 붙이는 기능만 추가하면 되는 간단한 과제로 보인다. 하지만 불친절하기 짝이 없는 42 교육 과정의 exam답게 본 시험에는 숨겨진 조건이 존재한다. 사실 tcp의 특성을 알고 있는 사람이라면 다음과 같은 의문이 들 것이다.

1. tcp 프로토콜은 임의로 자신이 필요하다고 판단할 시(ex. 한 번에 송신하기에는 너무 대량의 데이터일 경우) 패킷을 분할하여 송신한다. 예를 들어 10000 바이트 길이의 데이터를 송신할 시 1000바이트씩 쪼개서 보내지는 것이 가능하다.
2. 데이터를 송신하는 쪽은 당연히 메시지가 온전히 보전되기를 바라고 송신할 것이다. 즉, 접두사(client : %d) 뒤의 데이터는 전송되기 전과 동일하기를 기대할 것이다.
3. 하지만 앞서 설명했듯이 패킷은 tcp 프로토콜에 의하여 임의로 분할될 수 있으므로 용량이 큰 메시지를 보낼 경우 높은 확률로 훼손된다. 분할된 메시지의 앞부분마다 접두사가 끼어들어 버리기 때문이다.

```
// client 0이 매우 긴 메시지를 보내는 상황이라고 가정하자

보내는 메시지 : vvvveeeerrrryyyy lllloooonnnngggg mmmmssssgggg

// 전송자는 다음과 같이 메시지가 전송되기를 바랄 것이다.

client 0: vvvveeeerrrryyyy lllloooonnnngggg mmmmssssgggg

// 하지만 현실은 다음과 같을 확률이 높다.

client 0: vvvveeeerrrryyyy client 0: lllloooonnnngggg client 0: mmmmssssgggg 

```

4. 일반적인 echo 서버는 위와 같은 걱정을 할 필요가 없다. 왜냐하면 접두사를 붙여서 보내지 않기 때문이다. 클라이언트에서 패킷을 분할해서 보내도 보내는 대로 받아서 send back하면 그만이다. 하지만 접두사를 앞에 붙여서 보내야 한다는 조건이 추가되는 순간 이는 중대한 문제가 된다. 분할된 패킷 사이에 들어가는 접두사는 불순물로 전락해버린다. 접두사는 메시지의 맨 앞에 단 한 번만 들어가야 한다.
5. 이와 같은 문제를 해결하는 가장 간단한 방법은 구분자(delimeter, seperator)을 지정하는 것이다. 예를 들어 마침표(.)를 구분자로 지정했다고 가정해보자. 그러면 메시지가 분할되어 도착해도 구분자가 없음을 확인한 후 버퍼에 저장해두었다가, 구분자가 도착하면 합쳐서 한꺼번에 처리하는 방식이 가능할 것이다.

```
// 메시지가 다음과 같이 분할되어 전송된다.

packet0: vvvveeeerrrryyyy
packet1: lllloooonnnngggg
packet2: mmmmssssgggg.

// 하지만 구분자(.)가 발견될 때까지 패킷은 전송되지 않고 버퍼에 저장된다.

buffer: vvvveeeerrrryyyy + lllloooonnnngggg + (waiting for '.' ....)

// 구분자가 도착하면 비로소 전송한다.

client 0: vvvveeeerrrryyyy lllloooonnnngggg mmmmssssgggg.

```

6. 그런데 subject에는 구분자가 무엇인지 명시되어 있지 않다.

결론부터 말하자면, exam 06을 통과하기 위해선 구분자를 지정해야 한다. subject에 명시가 되어있지 않더라도 말이다. exam 06의 test case 08을 통과하기 위해서는 약 36만 바이트 길이의 메시지를 문제없이 echo 시킬 수 있어야 한다. 당연히 메시지는 분할되어서 들어올 것이고, 구분자를 지정하지 않으면 echo되는 메시지 사이사이에는 client: %d이 덕지덕지 붙어있을 것이다.

그나마 exam 06은 trace를 제공해주기 때문에, subject에 명시가 안되어 있는 구분자가 무엇인지 trace를 뜯어서 알아맞히는 식의 접근이 가능하다. 하지만 문제는 trace가 영어도 아니고 프랑스어로 되어있다는 점이다. 그리고 그렇게 자세히 나와있지도 않다. 따라서 사전 지식 없이 exam 06을 보는 사람은 높은 확률로 모르면 뒤져야지 당할 확률이 높다.

여러 삽질을 한 끝에 알아낸 결과

**mini_serv는 개행(\n)을 구분자로 삼아 메시지를 처리해야 한다.**

사실 subject 폴더에서 제공하는 main.c의 extract_message 함수에 개행을 기준으로 메시지를 추출하는 기능이 구현되어 있기 때문에 이게 힌트라면 힌트였던 셈이다.

즉, exam 06은 추가적으로 다음의 조건을 따라야 한다.

1. 수신받은 메시지에 개행이 포함되어 있다면 그냥 평범하게 send back 하면 된다.
2. 수신받은 메시지에 개행이 포함되어 있지 않다면 버퍼에 저장해두었다가 나중에 구분자가 도착했을 때 합쳐서 보내야 한다. 따라서 클라이언트마다 별개로 버퍼가 존재해야 하고, 새로운 클라이언트가 서버에 접속할 때마다 버퍼도 새로 만들어야 한다.
3. subject에는 이런 내용이 포함되어 있다.
	- a single message can contains multiple \n
	- 하나의 메시지에는 여러 개의 개행(\n)이 포함될 수 있다.
	-> 이러한 경우, 개행을 기준으로 서버가 메시지를 직접 분할하여 송신해야 한다.

## 자기 자신에게는 send back하지 마세요

subject에는 다음과 같은 조건이 있다.

- when the server receive a message, it must resend it to all the ==other== client with "client %d: " before every line!
- 서버가 메시지를 수신할 때, ==다른== 모든 클라이언트에게 "client %d: "를 접두사로 붙여 해당 메시지를 broadcast해야 합니다.

위 문장에서 ==다른==에 강조를 건 이유는, 자기 자신에게는 send back 하지 말아야 하기 때문이다.

예를 들어 서버에 클라이언트 1, 2, 3, 4, 5가 접속하고 있는 상황을 가정해보자.
1이 보낸 메시지는 2, 3, 4, 5에게는 전달되어야 하지만, 메시지를 보낸 당사자인 1에게는 전달되지 말아야 한다.

참고로 이 조건은 클라이언트가 서버에 접속할 때 보내지는 메시지, 클라이언트가 연결을 해제했을 때의 메시지에도 해당한다.

즉, 클라이언트는 서버와 연결을 끊을 때 자기 자신의 left 메시지를 받지 못하며(사실 이건 당연하다), 서버에 접속했을 때 자기 자신의 arrive 메시지를 받지 못한다.

---

이 문서를 읽으시는 모든 분들은 저처럼 시간 낭비하지 마시고 1트에 mini_serv 통과하시길 바랍니다.