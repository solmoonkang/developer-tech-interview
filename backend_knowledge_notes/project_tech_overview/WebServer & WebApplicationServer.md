![Static Content & Dynamic Content](/backend_knowledge_notes/image_files/WebServer%20&%20WebApplicationServer/static&dynamic.png)

## 정적 페이지, Static Pages

---

정적 페이지는 내용이 바뀌지 않는 항상 동일한 내용을 갖는 페이지를 의미한다. WebServer는 파일 경로 이름을 받아서 경로와 일치하는 file contents를 반환한다.

따라서 정적 페이지로는 image, html, css, javascript 파일과 같이 컴퓨터에 저장되는 파일들이다.

## 동적 페이지, Dynamic Pages

---

동적 페이지는 인자에 따라 내용이 변경되는 페이지를 의미한다. 즉, 인자의 내용에 맞게 동적인 contents를 반환한다.

따라서 웹 서버에 의해 실행되는 프로그램을 통해 만들어진 결과물이다.

## 웹 서버, Web Server(WS)

---

웹 서버는 인터넷을 기반으로 클라이언트에게 웹 서비스를 제공하는 컴퓨터이다.

웹 브라우저(클라이언트)로부터 HTTP 요청을 받아 정적인 컨텐츠(.html, .jpeg, css 등)를 제공한다.

- 클라이언트: 웹 서버에게 주소를 통신 규칙에 맞게 요청하면, 알맞은 내용(HTML)을 응답 받는다.
- 서버: 클라이언트의 요청을 기다리고, 웹 요청(HTTP)에 대한 데이터를 만들어서 응답한다.
   - 이때, 데이터는 웹에서 처리할 수 있는 HTML, CSS, 이미지 등 정적인 데이터로 한정된다.

### 웹 서버의 기능

---

HTTP 프로토콜을 기반으로 하여 클라이언트(웹 브라우저 또는 웹 크롤러)의 요청 서비스를 담당한다.

웹 서버는 요청에 따라서 두 가지 기능 중 적절하게 선택하여 수행한다.

- 첫 번째 기능은 정적인 컨텐츠를 제공한다. 따라서 WAS를 거치지 않고 바로 자원을 제공한다.
- 두 번째 기능은 동적인 컨텐츠 제공을 위한 요청을 전달한다.
   - 클라이언트의 요청을 WAS에 보내고, WAS가 처리한 결과를 클라이언트에게 전달(응답)한다.
- 웹 서버는 대표적으로 Apache Server, Nginx, IIS 등이 존재한다.

## 웹 애플리케이션 서버, Web Application Server(WAS)

---

WAS는 DB 조회나 다양한 로직 처리를 요구하는 동적인 컨텐츠를 제공하기 위해 만들어진 서버이다.

HTTP를 통해 컴퓨터나 장치에 애플리케이션을 수행해주는 미들웨어(소프트웨어 엔진)이다.

WAS는 웹 컨테이너 혹은 서블릿 컨테이너라고도 불린다.

- 여기서 컨테이너란 JSP, Servlet을 실행시킬 수 있는 소프트웨어를 의미한다.
- 즉, WAS는 JSP, Servlet 구동 환경을 제공한다.

### 웹 애플리케이션의 역할

---

WAS는 Web Server + Web Container를 합친 역할을 한다.

WAS는 Web Server 기능들을 구조적으로 분리하여 처리하고자 하는 목적으로 제시되었다.

- 때문에, 분산 트랜잭션, 보안, 메시징, 쓰레드 처리 등의 기능을 처리하는 분산 환경에서 사용된다.
- 주로 DB 서버와 함께 수행된다.

현재는 WAS가 가지고 있는 Web Server도 정적인 컨텐츠를 처리하는데 있어 큰 성능 차이는 없다.

### 웹 애플리케이션의 주요 기능

---

WAS는 프로그램 실행 환경과 DB 접속 기능을 제공하며, 여러 개의 트랜잭션을 관리하는 기능을 담당한다.

또한 업무를 처리하는 비즈니스 로직을 수행하는 역할을 한다.

대표적인 WAS는 Tomcat, JBoss, Jeus, Web Sphere 등이 존재한다.


## 웹 서버와 웹 애플리케이션 서버의 동작 과정

---

![Web Application Server Architecture](/backend_knowledge_notes/image_files/WebServer%20&%20WebApplicationServer/web-application-server.png)

## 웹 서버와 웹 애플리케이션 서버의 필요성

### 웹 서버가 필요한 이유

---

예를 들어, 클라이언트에 이미지 파일(정적인 컨텐츠)을 보내는 과정에서 이미지 파일과 같은 정적인 파일들은 웹 문서(HTML)가 클라이언트로 보내질 때 함께 전달되지 않는다.

1. 클라이언트는 HTML 문서를 받고, 그에 맞는 필요한 이미지 파일들을 다시 서버로 요청할 때 전달된다.
2. 때문에 웹 서버를 통해 정적인 파일들을 웹 애플리케이션 서버까지 가지 않고 앞단에서 처리할 수 있다.

따라서, 웹 서버에서는 정적인 컨텐츠만 처리하도록 기능을 분배하여 서버의 부담을 줄일 수 있다.

### 웹 애플리케이션 서버가 필요한 이유

---

웹 페이지는 정적 컨텐츠와 동적 컨텐츠 모두 존재하는데, 사용자 요청에 맞는 동적 컨텐츠를 제공해야 한다.

이때, 웹 서버만으로는 사용자가 원하는 요청에 대한 결과값을 내줄 수 없어 미리 만들어 서비스를 해야 한다.
- 하지만, 이렇게 수행할 경우 자원이 부족해진다.

따라서, 웹 애플리케이션 서버를 통해 요청에 맞는 데이터를 DB에서 가져와 비즈니스 로직에 맞게 그때 그때 알맞은 결과를 만들어 제공하여 자원을 효율적으로 사용할 수 있다.

### 웹 애플리케이션 서버가 웹 서버의 기능도 모두 수행할 경우

---

1. 기능을 분리하여 서버 부하 방지

   WAS는 DB 조회나 다양한 로직을 처리하기 때문에 단순 정적 컨텐츠는 웹 서버에서 처리하는 것이 좋다.
 
   WAS는 기본적으로 동적 컨텐츠를 제공하기 위해 존재하는 서버이다.

   만약, 정적 컨텐츠까지 처리한다면, 부하가 커지고 때문에 동적 컨텐츠 처리도 지연되어 속도가 느려진다.


2. 물리적으로 분리하여 보안 강화

   SSL에 대한 암복호화 처리에 웹 서버를 사용한다.


3. 여러 대의 WAS 연결 가능

   로드 밸런싱을 위해 웹 서버를 사용하며, Fail Over(장애 극복), Fail Back 처리에 유리하다.
   대용량 웹 애플리케이션의 경우(여러 개의 서버를 사용할 경우) 웹 서버와 웹 애플리케이션 서버를 분리하여 무중단 운영으로 장애 극복에 쉽게 대응할 수 있다.


4. 여러 웹 애플리케이션 서비스 기능

   예를 들어, 하나의 서버에서 PHP Application과 Java Application을 함께 사용할 수 있다.

5. 그 외 기능

   접근 허용 IP 관리 및 2대 이상의 서버에서의 세션 관리 등을 웹 서버에서 처리하면 효율적이다.


즉, 자원 이용의 효율성 및 장애 극복, 배포 및 유지보수의 편의성을 위해 WS와 WAS를 서로 분리한다.

WS를 WAS 앞에 두어 필요한 WAS들을 WS에 플러그인 형태로 설정하면 더욱 효율적인 분산 처리가 된다.

## 웹 서버의 동작 과정

---

![Web Server Architecture](/backend_knowledge_notes/image_files/WebServer%20&%20WebApplicationServer/web-server.png)

웹 서버 아키텍처는 다양한 구조로 동작할 수 있다.

1. 클라이언트 → 웹 서버 → 데이터베이스
2. 클라이언트 → 웹 애플리케이션 서버 → 데이터베이스
3. 클라이언트 → 웹 서버 → 웹 애플리케이션 서버 → 데이터베이스

### 클라이언트 → 웹 서버 → 웹 애플리케이션 서버 → 데이터베이스 구조의 동작 과정

---

1. 웹 서버는 웹 브라우저(클라이언트)로부터 HTTP 요청을 받는다.
2. 웹 서버는 클라이언트로부터 받은 요청을 웹 애플리케이션 서버로 보낸다.
3. 웹 애플리케이션 서버는 관련된 Servlet을 메모리에 올린다.
4. 웹 애플리케이션 서버는 `web.xml`을 참조하여 해당 Servlet에 대한 스레드를 생성한다.
5. HttpServletRqeust와 HttpServletResponse 객체를 생성하여 Servlet에 전달한다.
   1. 스레드는 Servlet의 `service( )` 메서드를 호출한다.
   2. `service( )` 메서드는 요청에 맞게 `doGet( )` 또는 `doPost( )` 메서드를 호출한다.
6. `doGet( )` 또는 `doPost( )` 메서드는 인자에 맞게 생성된 적절한 동적 페이지를 HttpServletResponse 객체에 담아서 웹 애플리케이션 서버에 전달한다.
7. 웹 애플리케이션 서버는 HttpServletResponse를 HttpResponse 형태로 바꿔 웹 서버에 전달한다.
8. 생성된 스레드를 종료하고, HttpServletRqeust와 HttpServletResponse 객체를 제거한다.

### 참고 자료
- [WebServer와 WebApplicationServer의 차이](https://dkswnkk.tistory.com/503)
- [WebServer와 WebApplicationServer란?](https://binux.tistory.com/32)
