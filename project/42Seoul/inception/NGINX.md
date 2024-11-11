
---

#web #server

*engine x*

---

**nginx**는 다음의 기능을 수행할 수 있는 프로그램이다.

- http 웹 서버
- 리버스 프록시
- 콘텐츠 캐시
- 로드 밸런서
- tcp/udp 프록시 서버
- 메일 프록시 서버

nginx는 하나의 **master 프로세스**와 여러 개의 **worker 프로세스**로 수행된다.

master 프로세스는 config 파일을 읽고 분석하며, worker 프로세스를 유지 및 관리한다.
worker 프로세스는 요청을 처리하는 작업을 담당한다.

nginx는 event-based 모델을 사용하며 운영체제(아마도 리눅스)에 의존적이다. 이는 worker 프로세스들에게 작업을 효율적으로 분배하기 위해서이다. worker 프로세스의 개수는 configuration 파일에서 정의되며 현재 가용한 cpu 코어 수에 따라 조정될 수 있다.

nginx가 동작하는 방식은 configuration 파일에 의해 정의된다. 일반적으로 configuration 파일은 `nginx.conf`라는 이름을 가지며 다음의 디렉토리 중 하나에 위치한다.

- `/usr/local/nginx/conf`
- `/etc/nginx`
- `/usr/local/etc/nginx`

## 시작, 정지, 그리고 설정 파일 리로딩

nginx를 시작하기 위해선 실행파일을 동작시킨다.

동작 중인 nginx를 제어하기 위해서는 -s 매개변수를 사용하여 응용 프로그램을 동작시킨다.
다음의 문법을 따른다.

`nginx -s <signal>`

**signal** 위치에는 다음의 인자들이 위치할 수 있다.

- stop : 빠른 강제 종료
- quit : 우아한(graceful) 종료
- reload : configuration file을 reload함
- reopen : log 파일을 다시 염

예를 들어, 현재 요청을 처리하기 위해 동작 중인 worker 프로세스들을 정지하기 위해서는 아래의 커맨드를 동작한다.

`nginx -s quit`

> 이 커맨드는 nginx를 실행시킨 유저와 동일한 유저에 의하여 호출되어야 한다.

configuration 파일이 수정되어도 그것이 reload 되거나 nginx가 다시 시작하기 전까지는 수정사항이 반영되지 않는다. configuration 파일을 reload 하려면 아래의 커맨드를 동작시킨다.

`nginx -s reload`

master 프로세스는 reload configuration 신호를 받으면, 수정된 configuration 파일의 유효성을 확인하고 변경사항을 적용한다.

이 작업이 성공한다면, master 프로세스는 새로운 worker 프로세스를 생성하고 기존에 존재하던 worker 프로세스에게는 종료 명령을 보낸다.

이 작업이 실패한다면, master 프로세스는 변경 사항을 롤백하고 기존 configuration 파일에 따라 작업을 계속한다.

종료 명령을 받은 worker 프로세스는 새로운 요청을 받는 것을 중단한 후, 제공하고 있던 요청(=서비스)를 마저 제공한다. 그런 후 exit 한다.

unix의 kill 유틸리티를 이용하여 신호를 보낼 수도 있다. 이 경우 신호를 보내고자 하는 프로세스의 id를 알아야 한다. nginx master 프로세스의 id는 일반적으로 `/usr/local/nginx/logs/nginx.pid`에 저장되어 있다.
아래와 같은 명령어를 사용한다.

`kill -s QUIT <nginx master process id>`

`ps` 명령을 통해 현재 동작 중인 nginx 프로세스들의 목록을 가져올 수도 있다.

`ps -ax | grep nginx`

## Configuration 파일의 구조

nginx는 configuration 파일에 열거된 지침(directives)을 따른다. 지시 사항은 단순한 지침(simple directives)와 블록 지침(block directives)로 나뉜다.

단순한 지침은 아래와 같은 형식을 취한다.

`name parameter;`

블록 지침은 다른 여러 개의 지침들을 `{`, `}`로 둘러싸는 형태로 보유할 수 있으며, 이를 context(문맥)라고 부른다(예 : events, http, server, location).

```
http {
	server {
	}
}
```

configuration 파일에 있는 모든 지침들은 어디에 위치해있던지 main context에 존재하는 것으로 간주한다(*오역의 가능성 있음*).

`#` 기호 뒤에 오는 문장은 주석으로 간주한다.

## 정적 컨텐츠 제공하기

웹 서버의 주요 업무는 이미지나 정적 html 페이지 같은 파일을 제공하는 것이다.

html 파일은 보통 `/data/www` 디렉토리에 위치해 있고
이미지 파일은 보통 `/data/images`에 위치해 있다.

http 블록 내부의 server 블록에 두 개의 location 블록을 설정함으로서 이를 설정할 수 있다.
아래와 같은 절차를 통해 예제를 진행해보자.

1. `/data/www` 디렉토리를 만든 후 그 안에 `index.html`을 위치시킨다. `index.html`에는 어떠한 내용이 있어도 괜찮다.
2. `/data/image` 디렉토리를 만든 후 그 안에 아무 이미지나 넣는다.
3. configuration 파일을 연다. 파일 안에는 이미 여러 개의 server 블록이 있을 것이고 그 중에서는 주석 처리가 된 것도, 그렇지 않은 것도 있을 것이다. 주석 처리되지 않은 모든 server 블록을 주석처리하고 아래와 같이 새로운 server 블록을 만든다.

	```
	http {
		server {
		}
	}
	```

> 일반적으로 configuration 파일 내부에는 수신하고 있는 포트 번호, 그리고 서버의 이름에 따라 여러 개의 server 블록이 있다. nginx는 요청의 헤더 부분에 있는 URI를 분석하여 server 블록 내부의 location 지침에 있는 인자와 대조함으로서 어느 서버가 요청을 수행할지를 결정한다.

4. 다음의 location 블록을 server 블록에 더한다.

	```
	location / {
		root /data/www;
	}
	```

	```
	location /images/ {
		root /data;
	}
	```

> URI의 경로는 root 지침의 인자와 location 지침의 인자를 조합한 결과물과 대조된다. `/data/images` 블록을 보면 경로가 역순으로 되어 있는데(하위 디렉토리인 /images/ 가 상단에 있고 상위 디렉토리인 /data/가 하단에 있음) 이는 탐색의 효율성을 위해서이다.
> 예를 들어 `/data/www`와 `/data/images`를 구별하는 것은 상위 디렉토리인 `/data`가 아니라 하위 디렉토리인 `/www`와 `/images`이다. 따라서 둘 중 `/data/www`를 탐색하는 경우 상위 디렉토리 -> 하위 디렉토리 순으로 검색하는 것보다 하위 디렉토리 -> 상위 디렉토리 순으로 검색하는 것이 빠를 것이다.
> 따라서 configuration 파일에서는 하위 디렉토리를 location 지침의 인자로, 상위 디렉토리를 root 지침의 인자로 전달한다.
> 참고로 configuration 파일은 인자의 길이가 긴 location 블록을 우선적으로 탐색한다.

위 과정이 완료되면 위 설정 파일은 80 포트(nginx의 기본 포트이다)로 웹 서비스를 제공하라는 의미를 가지게 된다.

`http://localhost/` 뒤에 `/images/`가 붙으면 `/data/images/`의 파일을 제공하게 된다.
- ex. `http://localhost/images/example.png` 주소는 `/data/images/example.png`를 제공하라는 뜻

`/images/` 외의 다른 경로는 `/data/www/`의 파일을 제공하게 된다.
- ex. `http://localhost/images/some/example.html`은 `/data/www/some/example.html`을 제공하라는 뜻

> 예상대로 작업이 수행되지 않는다면 `access.log`와 `error.log` 파일에 이유가 기록되어 있을 수 있다. 두 파일은 보통 `/usr/local/nginx/logs`나 `/var/log/nginx`에 위치해 있다.

## 간단한 프록시 서버 구축하기



---

참고자료

#참고링크/nginx_org 

---