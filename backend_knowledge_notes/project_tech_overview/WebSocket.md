## 웹 소켓의 등장 배경

---

초기 인터넷의 통신 방식은 주로 HTTP를 이용한 클라이언트-서버 모델을 통해 진행되었다.

- 즉, 클라이언트가 서버에 요청을 보내고, 서버가 이에 응답하는 통식 방식을 따른다.

하지만 이러한 방식은 실시간으로 데이터를 주고 받을 때 한계점이 발생하게 된다.

- 요청과 응답이 있다는 것은 클라이언트가 서버에게 요청하지 않는 이상
- 서버는 클라이언트에게 먼저 데이터를 보낼 수 없게 된다.

때문에 클라이언트는 새로운 데이터가 있는지 확인하기 위해 서버에 지속적으로 요청을 보낼 수 밖에 없다.

- 그렇게 되면 불필요한 트래픽이 증가되고, 이로 인해 서버의 비용이 증가하게 된다.
- 뿐만 아니라 요청과 응답 사이의 지연시간으로 실시간 통신의 효율성을 저하시킬 수 있다.

이러한 상황을 방지하고 해결하기 위해 등장한 것이 웹 소켓이다.

## 웹 소켓이란?

---

![WebSocket](/backend_knowledge_notes/image_files/WebSocket/web-socket.png)

웹 소켓은 HTML5에 등장한 실시간 웹 애플리케이션을 위해 설계된 통신 프로토콜이다.

- 웹 소켓은 TCP를 기반으로 동작한다.
- 때문에 신뢰성 있는 데이터 전송을 보장하며, 메시지 경계를 존중하고, 순서가 보장된 통신이다.

따라서 웹 소켓은 HTTP와 다르게 클라이언트-서버 간 최초 연결이 이루어지면 양방향 통신을 할 수 있다.

웹 소켓은 지속적 연결을 통해 서버→클라이언트 혹은 클라이언트→서버로 데이터를 보낼 수 있다.

- 이때 데이터는 패킷 단위로 전송되며, 연결 중단과 추가 HTTP 요청 없이 양방향으로 이루어진다.

## 웹 소켓 이전의 비슷한 기술

---

### Polling 방식

![Polling](/backend_knowledge_notes/image_files/WebSocket/polling.png)

Polling은 서버로 일정 주기로 요청을 송신하는 기술이다.

- 실시간 통신에서는 언제 통신이 발생할지 예측이 불가능하다.
- 불필요한 요청과 커넥션을 생성한다.

때문에 실시간 통신이라고 부르기 애매할 정도의 실시간성을 가지고 있다.

### Long Polling 방식

![Long-Polling](/backend_knowledge_notes/image_files/WebSocket/long-polling.png)

Long Polling은 Polling의 단점을 최소화하기 위해 서버에서 조금 더 대기해서 이벤트를 받는다.

- 서버에 요청을 보내고 이벤트가 생겨 응답을 받을 때까지 연결이 종료되지 않는다.

하지만 많은 양의 메시지가 쏟아지면 Polling과 같아진다.

### Streaming 방식

![Streaming](/backend_knowledge_notes/image_files/WebSocket/streaming.png)

Streaming은 서버에 요청을 보내고 끊기지 않은 연결 상태에서 끊임없이 데이터를 수신한다.

하지만 클라이언트에서 서버로의 데이터 송신이 어렵다.

결과적으로 모든 방법들이 HTTP를 통해 통신하기 때문에 요청과 응답 모두 헤더가 불필요하게 크다.

## 웹 소켓 동작 방법

---

웹 소켓 또한 핸드-쉐이크 과정이 이루어지고, 소켓 프로토콜이 아닌 HTTP 또는 HTTPS로 통신하게 된다.

![WebSocket Architecture](/backend_knowledge_notes/image_files/WebSocket/web-socket-architecture.png)

```bash
GET /socket
Host: yong-nyong-tistory.com
Origin: https://yong-nyong-tistory.com
Connection: Upgrade
Upgrade: websocket
Sec-WebSocket-Key: Ivyio/9s+lYongNyongczP8Q==
Sec-WebSocket-Version: 13
```

웹 소켓 요청은 HTTP 버전 1.1 이상에서 동작한다. 또한 반드시 GET 메서드를 사용해야 한다.

- **Origin**은 클라이언트의 출처를 나타낸다.
- **Connection-Upgrade**는 클라이언트 측에서 프로토콜을 바꾸고 싶다는 신호를 보낸 것이다.
- **Upgrade-websocket**은 클아이언트 측에서 요청한 프로토콜이 웹 소켓이라는 것이다.
- **Sec-WebSocket-Key**는 브라우저에서 생성한 키로, 서버가 웹 소켓을 지원하는지 확인한다.
- **Sec-WebSocket-Version**은 웹 소켓 프로토콜 버전을 나타낸다.

```bash
101 Switching Protocols
Upgrade: websocket
Connection: Upgrade
Sec-WebSocket-Accept: hsBYongNyong24s99EO10UlZ22C2g=
```

웹 소켓 응답은 101 Switching Protocols가 응답으로 오게 되면 웹 소켓이 연결된 것이다.

- Sec-WebSocket-Accept는 요청에서의 Key값을 계산한 값으로 신원 인증에 필요한 헤더이다.

![WebSocket Hand-Shake](/backend_knowledge_notes/image_files/WebSocket/web-socket-handshake.png)

위와 같이 핸드-쉐이크 과정이 완료되면 프로토콜이 WS로 변경된다.

- 데이터 보안을 위해 SSL을 적용한다면 WSS 프로토콜로 변경된다.

웹 소켓이 정상적으로 생성되면, 아래와 같은 네 개의 이벤트를 사용할 수 있게 된다.

- **OPEN**: 연결이 성공적으로 이루어졌을 때 발생한다.
- **MESSAGE**: 데이터를 수신했을 때 발생한다.
- **ERROR**: 연결 중 에러가 생겼을 때 발생한다.
- **CLOSE**: 연결이 종료되었을 때 발생한다.

## 웹 소켓의 한계

---

- 웹 소켓은 HTML5 사양의 일부로, HTML5를 지원하지 않는 브라우저에서는 사용할 수 없다.
- 지속적인 연결을 유지하므로, 많은 웹 소켓 연결을 동시 관리할 경우 서버 부하가 증가할 수 있다.
- 만약, 연결이 끊어지면 어떤 이유로 연결이 끊어졌는지와 같은 상세 에러 처리에 대한 한계가 존재한다.
- 자동 재연결을 진행하지 않아 에러로 연결이 끊어지면 연결을 위해 재연결을 하도록 구현해야 한다.

### 참고 자료
- [웹 소켓이란?](https://velog.io/@codingbotpark/Web-Socket-%EC%9D%B4%EB%9E%80)
- [웹 소켓이란? 등장 배경과 목적, 동작 방식](https://yong-nyong.tistory.com/90)
