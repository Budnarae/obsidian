
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
만약에 당신이 메모리를 할당할 수 없다면 표준 오류로 "Fatal error"에 개행(\n)을 붙여 출력하고 exit status 1로 종료

Your program must be non-blocking but client can be lazy and if they don't read your message you must NOT disconnect them...

Your program must not contains #define preproc
Your program must only listen to 127.0.0.1
The fd that you will receive will already be set to make 'recv' or 'send' to block if select hasn't be called before calling them, but will not block otherwise. 

When a client connect to the server:
- the client will be given an id. the first client will receive the id 0 and each new client will received the last client id + 1
- %d will be replace by this number
- a message is sent to all the client that was connected to the server: "server: client %d just arrived\n"

clients must be able to send messages to your program.
- message will only be printable characters, no need to check
- a single message can contains multiple \n
- when the server receive a message, it must resend it to all the other client with "client %d: " before every line!

When a client disconnect from the server:
- a message is sent to all the client that was connected to the server: "server: client %d just left\n"

Memory or fd leaks are forbidden

To help you, you will find the file main.c with the beginning of a server and maybe some useful functions. (Beware this file use forbidden functions or write things that must not be there in your final program)

Warning our tester is expecting that you send the messages as fast as you can. Don't do un-necessary buffer.

Evaluation can be a bit longer than usual...

Hint: you can use nc to test your program
Hint: you should use nc to test your program
Hint: To test you can use fcntl(fd, F_SETFL, O_NONBLOCK) but use select and NEVER check EAGAIN (man 2 send)

