
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

## 

---

참고자료

#참고링크/nginx_org 

---