### 🧑🏼‍🌾 면접 질문 정리

신입 개발자 및 기술 면접 준비를 위한 질문들을 정리하고 학습하는 공간입니다.

✨ 해당 저장소에 포함된 내용은 제가 직접 공부한 내용을 바탕으로 정리한 것이므로, 정확하지 않을 수 있습니다.  
따라서 참고용으로만 사용하시고, 추가적인 자료를 통해 확인하시기를 권장합니다.

[백엔드 개발 기술 면접 | 신입 개발자 단골 질문](#신입-개발자-단골-질문)
<details>
<summary>JAVA 단골 질문</summary>

- [1. 컴파일 과정을 말해주세요.](#컴파일-과정)
- [2. String, StringBuilder, StringBuffer의 차이점에 대해 말해주세요.](#string-stringbuilder-stringbuffer의-차이)
- [3. Java의 접근 제어자의 종류와 특징](#java의-접근-제어자의-종류와-특징)
- [4. OOP의 4가지 특징에 대해서 말해주세요.](#oop의-4가지-특징)
- [5. OOP의 5대 원칙 (SOLID)에 대해서 말해주세요.](#oop의-5대-원칙-solid)
- [6. JVM의 구조에 대해서 말해주세요.](#jvm의-구조)
- [7. 클래스, 객체, 인스턴스의 차이에 대해서 말해주세요.](#클래스-객체-인스턴스의-차이)
- [8. Interface와 Abstract Class의 차이에 대해서 말해주세요.](#interface와-abstract-class의-차이)
- [9. CheckedException과 UnCheckedException의 차이에 대해서 말해주세요.](#checkedexception과-uncheckedexception의-차이)
- [10. Call By Reference와 Call By Value의 차이에 대해서 말해주세요.](#call-by-reference와-call-by-value의-차이)
- [11. 오버로딩과 오버라이딩의 차이에 대해서 말해주세요.](#오버로딩과-오버라이딩의-차이)

</details>
<details>
<summary>SPRING 단골 질문</summary>

- [1. Spring 프레임워크에 대해 말해주세요.](#spring-프레임워크)
- [2. 제어의 역전(Inversion of Control, IoC)에 대해 말해주세요.](#제어의-역전inversion-of-control-ioc)
- [3. 의존성 주입(Dependency Injection, DI)에 대해 말해주세요.](#의존성-주입dependency-injection-di)
- [4. 스프링 빈(Spring Bean)에 대해 말해주세요.](#스프링-빈spring-bean)
- [5. 스프링 MVC에 대해서 말해주세요.](#스프링-mvc)
- [6. Spring Boot 프레임워크에 대해 말해주세요.](#spring-boot-프레임워크)
- [7. 스프링 AOP에 대해 말해주세요.](#스프링-aop)
</details>
<details>
<summary>️JPA 단골 질문</summary>

- [1. JPA, Hibernate, 그리고 Spring Data JPA의 차이에 대해 말해주세요.](#jpa-hibernate-그리고-spring-data-jpa의-차이)
- [2. JPA 엔티티 생명 주기에 대해 말해주세요.](#jpa-엔티티-생명-주기)
- [3. 영속성 컨텍스트에 대해 말해주세요.](#영속성-컨텍스트-persistence-context)
- [4. 1차 캐시와 2차 캐시의 차이에 대해 말해주세요.](#1차-캐시-first-level-cachel1-cache와-2차-캐시-second-level-cachel2-cache)
- [5. JPA에서 연관관계 설정 시 일대일, 일대다, 다대일, 다대다의 차이에 대해 말해주세요.](#jpa-연관관계-종류)
- [6. JPA 상속 관계 매핑 전략에 대해 말해주세요.](#jpa-상속-관계-매핑)
- [7. JPQL(Java Persistence Query Language)에 대해 말해주세요.](#객체-지향-쿼리-언어)
- [8. 트랜잭션, Transaction에 대해 말해주세요.](#트랜잭션-transaction)
- [9. JPA 프록시 객체에 대해 말해주세요.](#jpa-프록시-객체)
- [10. 쓰기 지연 SQL 저장소에 대해 말해주세요.](#sql-실행-최적화)
</details>
<details>
<summary>BACK-END 단골 질문</summary>

- [1. HTTP 메서드에 대해 말해주세요.]()
- [2. HTTP 상태 코드에 대해 말해주세요.]()
- [3. REST API 설계 원칙에 대해 말해주세요.]()
</details>


[백엔드 개발 기술 면접 | 프로젝트 관련 질문](#프로젝트-관련-질문)
<details>
<summary>Redis 관련 질문</summary>

- [1. Redis란 무엇이며, 어떤 주요 기능을 제공하는지 말해주세요.](#redis-개념)
- [2. Redis가 메모리 기반 저장소인 이유와 그 이점에 대해 말해주세요.](#메모리-기반-저장소인-이유-및-이점)
- [3. Redis에서 지원하는 주요 데이터 구조에 대해 말해주세요.](#redis의-데이터-구조)
- [4. Redis의 데이터 지속성 기능에 대해 말해주세요.](#redis의-데이터-지속성)
- [5. Redis가 높은 성능과 원자성을 보장하는 방법에 대해 말해주세요.](#redis의-성능-및-원자성-보장)
- [6. Redis의 복제와 클러스터링 기능에 대해 말해주세요.](#redis-복제-및-클러스터링)
- [7. Redis의 Pub/Sub 기능은 무엇이며, 어떻게 활용할 수 있는지 말해주세요.](#redis의-pub-sub)
- [8. Redis에서 Lua 스크립팅을 지원하는 이유와 그 장점에 대해 말해주세요.](#reids의-lua-스크립팅)
- [9. Redis를 캐시로 활용할 때 고려해야 할 사항에 대해 말해주세요.](#redis-캐시-활용-시-고려사항)
- [10. Redis를 실제 프로젝트에 도입할 때 겪었던 어려움과 이를 어떻게 해결하였는지 사례를 말해주세요.]()
</details>
<details>
<summary>WebSocket 관련 질문</summary>

- [1. 웹소켓이란 무엇이며, 기존의 HTTP 통신 방식과 어떤 차이가 있는지에 대해 말해주세요.](#웹소켓의-정의-http-통신과의-차이점)
- [2. 웹소켓 핸드셰이크 과정은 어떻게 이루어지며, 어떤 헤더들이 사용되는지에 대해 말해주세요.](#웹소켓-핸드셰이크-과정)
- [3. 웹소켓 연결을 유지하는 방법과 Ping-Pong 메커니즘에 대해 말해주세요.](#웹소켓-연결-유지)
- [4. 웹소켓의 주요 장점과 한계는 무엇인지 말해주세요.](#웹소켓-장점-및-한계)
- [5. 웹소켓 프로토콜이 메시지 프레이밍을 어떻게 처리하는지 말해주세요.](#웹소켓-메시지-프레이밍)
- [6. 보안 측면에서 웹소켓 사용 시 고려해야 할 사항에 대해 말해주세요.](#웹소켓-사용-시-고려-사항)
- [7. 대규모 트래픽 환경에서 웹소켓의 확장성을 확보하기 위한 전략에 대해 말해주세요.](#웹소켓-확장성-전략)
- [8. STOMP와 같은 메시징 프로토콜을 웹소켓에 도입하는 이유와 그 장점에 대해 말해주세요.](#stomp-프로토콜-도입-이유-및-장점)
- [9. 웹소켓 연결이 예기치 않게 끊어졌을 때, 클라이언트와 서버 측에서는 어떤 재연결 전략을 사용할 수 있는지에 대해 말해주세요.](#웹소켓-재연결-전략)
- [10. 웹소켓을 실제 프로젝트에 도입할 때 겪었던 어려움과 이를 어떻게 해결하였는지 사례를 말해주세요.]()
</details>

[백엔드 개발 기술 면접 | CS 단골 질문](#cs-단골-질문)
<details>
<summary>JAVA 관련 질문</summary>

</details>
<details>
<summary>SPRING 관련 질문</summary>

</details>
<details>
<summary>JPA 관련 질문</summary>

</details>
<details>
<summary>DATABASE 관련 질문</summary>

</details>
<details>
<summary>NETWORK 관련 질문</summary>

</details>
<details>
<summary>OS 관련 질문</summary>

</details>

---

#### REFERENCE
- [자바 기술 면접 대비하기 - 1편](https://f-lab.kr/blog/java-backend-interview-1)
- [자바 기술 면접 대비하기 - 2편](https://f-lab.kr/blog/java-backend-interview-2)
- [자바 개발자 면접 가이드 - 1편](https://careerly.co.kr/comments/100242)
- [자바 개발자 면접 가이드 - 2편](https://careerly.co.kr/comments/100476)
