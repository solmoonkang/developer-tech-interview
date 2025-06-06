## Nginx란?

---

Nginx는 트래픽이 많은 웹 사이트의 서버를 도와주는 비동기 이벤트 기반 구조 경량화 웹 서버 프로그램이다.

- 클라이언트로부터 받은 요청에 맞는 정적 파일을 응답해주는 HTTP Web Server로 활용된다.
- 또한 리버스 프록시 서버로 활용하여 WAS의 부하를 줄이는 로드밸러스 역할을 한다.

## Nginx가 만들어진 배경

---

1995년 UNIX 기반으로 만들어진 NCSA HTTPd 웹 서버가 있었지만, 버그가 많아 불편함이 컸다.

- 그래서 이를 해결하기 위해 만들어진 것이 Apache Server이다.
- Apache Server는 요청이 들어오면 커넥션을 생성한다.

![NGINX PREFORK](/backend_knowledge_notes/image_files/NGINX/nginx-prefork.png)

하지만 프로세스를 생성하는 과정이 오랜 시간이 걸려 프로세스를 미리 만드는 PREFORK 방식을 이용한다.

- 새로운 클라이언트 요청이 오면 미리 만들어놓은 프로세스를 할당한다.
- 만약, 만들어놓은 프로세스가 없다면 추가로 프로세스를 생성했다.

이러한 구조 덕분에 개발자는 다양한 모듈을 만들어 서버에 빠르게 기능을 추가할 수 있었다.

- 즉, 확장성이 높았고, Apache Server는 동적 컨텐츠를 처리할 수 있게 되었다.
- 이는 요청을 받고 응답을 처리하는 과정을 하나의 서버에서 해결하기 좋았다.

하지만 1999년에 들어서면서 컴퓨터가 많이 보급됨에 따라 요청이 많아져서 서버에 동시에 연결된 커넥션이 많을 때 더 이상 새로운 커넥션을 생성하지 못하게 되었다.

![NGINX C10K Problem](/backend_knowledge_notes/image_files/NGINX/nginx-c10k.png)

이를 C10K라고 하는데, 이는 커넥션 10000개의 문제라는 의미로, 다음과 같은 문제점이 있었다.

1. **메모리 부족**: 커넥션이 연결될 때마다 프로세스를 생성한다.
2. **무거운 프로그램**: 확장성이 좋다는 건 곧 리소스가 많다는 것을 의미한다.
3. **CPU 부하 증가**: 많은 커넥션 요청이 들어오면 Context Switching을 많이 하여 CPU 부하가 증가한다.

즉, Apache Server는 현대로 올수록 사용하기 꺼려졌고, 이런 구조적 문제점을 해결한 Nginx가 등장한다.

초창기 Nginx는 Apache와 함께 사용하기 위해 만들어졌다.

- Nginx는 웹 서버이기는 하지만 Apache 서버를 완전히 대체할 목적은 아니었다.
- Apache 서버가 지닌 구조적 한계를 Nginx를 사용하면서 극복하려고 했다.

![Apache & NGINX](/backend_knowledge_notes/image_files/NGINX/apache+nginx.png)

수많은 동시 커넥션을 Nginx가 유지하고, Nginx도 웹 서버이기에 정적 파일에 대한 요청은 스스로 처리했다.

또한, 클라이언트로부터 동적 파일의 요청을 받았을 때만 Apache 서버와 커넥션을 형성하여 Apache 서버의 부하를 줄였다.

## Nginx의 구조

---

Nginx는 설정파일을 읽고, 설정에 맞게 Worker Process를 생성하는 Master Process가 있다.

- Worker Process는 실제로 작업을 하는 프로세스이며,
- Worker Process가 만들어질 때 지정된 Listen 소켓을 배정받는다.
- 해당 소켓에 새로운 클라이언트의 요청이 들어오면 커넥션을 형성하고 처리한다.

커넥션은 정해진 Keep-Alive 시간만큼 유지된다.

하지만 커넥션이 형성되었다고 해서 Worker Process가 해당 커넥션 하나만 담당하지는 않는다.

- 형성된 커넥션으로부터 아무런 요청이 없다면 새로운 커넥션을 형성하거나
- 이미 만들어진 다른 커넥션으로부터 들어온 요청을 처리한다.

Nginx에서는 이러한 커넥션 형성과 제거, 그리고 새로운 요청을 처리하는 것을 이벤트(Event)라고 한다.

이러한 이벤트들은 OS 커널이 Queue 형식으로 Worker Process에게 전달한다.

- 이벤트들은 Queue에 담긴 상태에서 비동기 상태로 대기한다.
- Worker Process는 하나의 스레드로 이벤트를 꺼내서 처리해 나간다.

이런 방식은 Worker Process가 쉬지 않고 일을 하기 때문에,

요청이 없을 때는 프로세스를 방치시키는 Apache 서버보다 훨씬 효율적으로 자원을 사용할 수 있다.

![Apache: 스레드 방식](/backend_knowledge_notes/image_files/NGINX/apache-thread.png)


![Nginx: Evnet-Driven 방식](/backend_knowledge_notes/image_files/NGINX/nginx-event.png)

Apache의 스레드 기반의 방식은 하나의 커넥션 당 하나의 스레드를 잡아먹게 된다.

반면, 이벤트 기반의 방식은 여러 개의 커넥션을 전부 EvnetHandler를 통해 비동기 방식으로 처리한다.

- **이러한 이벤트 기반 구조가 Nginx의 핵심이다.**

## Nginx의 특징

---

Nginx는 기본적으로 동적 컨텐츠를 처리할 수 없다는 단점을 가지고 있다.

- 동적 컨텐츠에 대한 PHP 및 기타 요청을 처리하려면 Nginx가 이를 실행하기 위해 외부 프로세스로 전달하고 렌더링된 컨텐츠가 다시 전송될 때까지 기다려야 한다.
- 이는 프로세스의 속도 저하를 야기시킨다.

즉, 동적 웹 페이지 컨텐츠를 가진 모든 요청을 위해 외부 자원과 연계한다. (PHP-FPM)

반면, Nginx는 이벤트 중심 접근 방식을 사용하여 클라이언트 요청을 제공한다.

또한, 제한된 하드웨어 리소스로도 여러 클라이언트 요청을 동시에 효율적으로 처리가 가능하다.

- 이는 단일 스레드를 통해 여러 연결 처리가 가능하다.

따라서, 최소한의 리소스로 웹 서버의 아키텍처를 개선하기 위해 독립형 HTTP 서버로 배치가 가능하다.

## Apache vs Nginx 성능 비교

---

![동시 커넥션 수당 메모리 사용률](/backend_knowledge_notes/image_files/NGINX/memory-usage.png)

동시 커넥션 수당 메모리 사용률

Apache 서버에 비해 Nginx는 동시 커넥션 수가 늘어나도 메모리 사용률이 낮고 일정함을 확인할 수 있다.

![동시 커넥션 수에 따라 처리되는 초당 요청 수](/backend_knowledge_notes/image_files/NGINX/requests-per-second.png)

동시 커넥션 수에 따라 처리되는 초당 요청 수

반면, 동시 커넥션 수가 많아졌을 때 처리하는 요청 수는 Nginx가 Apache 서버에 비해 압도적으로 높다.

### 참고 자료
- [NGINX란?](https://dkswnkk.tistory.com/513)
