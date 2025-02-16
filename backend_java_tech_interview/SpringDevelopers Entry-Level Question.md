### 백엔드 개발 자바 기술 면접 | 신입 개발자 SPRING 단골 질문

---

- [1. Spring 프레임워크에 대해 말해주세요.](#spring-프레임워크)
    - [1-1. Spring 프레임워크를 사용하는 이유에 대해 말해주세요.]()
    - [1-2. Spring 프레임워크의 핵심 모듈이 무엇인지 말해주세요.]()
- [2. 제어의 역전(Inversion of Control, IoC)에 대해 말해주세요.](#제어의-역전inversion-of-control-ioc)
    - [2-1. IoC 컨테이너에 대해 말해주세요.]()
- [3. 의존성 주입(Dependency Injection, DI)에 대해 말해주세요.](#의존성-주입dependency-injection-di)
    - [3-1. 스프링의 의존성 주입 방식에 대해 말해주세요.]()
- [4. 스프링 빈(Spring Bean)에 대해 말해주세요.](#스프링-빈spring-bean)
    - [4-1. 스프링 빈을 정의하는 방법에 대해 말해주세요.]()
    - [4-2. 스프링 빈의 생명주기에 대해 말해주세요.]()
    - [4-3. @Component, @Service, @Repository, @Controller 어노테이션의 차이점에 대해 말해주세요.]()
- [5. 스프링 MVC에 대해서 말해주세요.](#스프링-mvc)
    - [5-1. DispatcherServlet에 대해 말해주세요.]()
    - [5-2. 스프링 MVC의 동작 과정에 대해 말해주세요.]()
- [6. Spring Boot 프레임워크에 대해 말해주세요.](#spring-boot-프레임워크)
    - [6-1. 스프링 부트를 사용하는 이유, 주요 특징에 대해서 말해주세요.]()
    - [6-2. 스프링 부트를 사용하는 장점에 대해 말해주세요.]()
    - [6-3. @SpringBootApplication 어노테이션에 대해 말해주세요.]()
    - [6-4. Spring Data JPA에 대해 말해주세요.]()
    - [6-5. Spring Repository에 대해 설명해주세요.]()
    - [6-6. CrudRepository와 JpaRepository의 차이에 대해 설명해주세요.]()
- [7. 스프링 AOP에 대해 말해주세요.](#스프링-aop)

<br>

#### Spring 프레임워크

<details>
<summary>Spring 프레임워크에 대해 말해주세요.</summary>

- **자바 기반의 엔터프라이즈 애플리케이션을 개발하기 위한 강력한 프레임워크**이다.
- IoC, DI, AOP 등 **다양한 기능을 제공**하여 개발자가 더 쉽게 유지보수 가능한 애플리케이션을 만들도록 돕는다.
    - 스프링은 특히 웹 애플리케이션, RESTful 서비스, 배치 처리 등 다양한 용도로 사용된다.

<details>
<summary>⁉️ Spring 프레임워크를 사용하는 이유에 대해 말해주세요.</summary>

- **IoC 및 DI**를 사용한 객체 관리의 수월함과 코드의 결합도가 감소한다.
- **모듈화 및 재사용성**으로 필요한 기능만 선택하여 사용할 수 있는 유연성이 있다.
- **AOP**를 사용하여 코드의 중복을 줄이고 가독성을 향상시킨다.
- 웹 애플리케이션 구축을 위해 **스프링 MVC 프레임워크**를 지원한다.
- Hibernate, JPA, EJB 등 다양한 기술과 쉽게 **통합**된다.

</details>

<br>

<details>
<summary>⁉️ Spring 프레임워크의 핵심 모듈이 무엇인지 말해주세요.</summary>

1. **Spring Core**: 제어의 역전(IoC)과 의존성 주입(DI) 기능을 제공한다.
2. **Spring AOP**: 관점 지향 프로그래밍을 제공한다.
3. **Spring ORM**: Hibernate, JPA 등 ORM 프레임워크와의 통합을 제공한다.
4. **Spring DAO**: 데이터베이스 상호작용을 간소화하는 JDBC 추상화 계층을 제공한다.
5. **Spring Context**: 스프링 애플리케이션에 대한 컨텍스트 정보를 제공한다.
6. **Spring Web**: 웹 지향 통합 기능을 제공한다.
7. **Spring MVC**: Model-View-Controller 아키텍처 및 구성 요소를 제공한다.

</details>

</details>

---

#### 제어의 역전(Inversion of Control, IoC)

<details>
<summary>제어의 역전(Inversion of Control, IoC)에 대해 말해주세요.</summary>

- 객체의 생성과 생명 주기를 외부에서 관리하는 원칙이다.
- 이에 개발자는 객체의 구현에 집중하고, IoC를 통해 객체의 관리와 의존성 주입을 외부에 맡긴다.

> 일반적으로 객체가 자신의 의존성을 스스로 생성하는 것과 반대되는 개념이다.

<details>
<summary>⁉️ IoC 컨테이너에 대해 말해주세요.</summary>

- IoC 원칙을 구현하는 스프링 프레임워크의 핵심 컴포넌트이다.
- 스프링 빈(Bean)의 생성, 의존성 주입, 생명 주기 관리 등을 담당한다.
- 스프링의 ApplicationContext와 BeanFactory가 대표적인 IoC 컨테이너이다.

> IoC 원칙을 실제로 구현하는 구체적인 시스템이나 도구이다. IoC를 적용하여 객체를 관리하는 역할을 한다.

</details>

</details>

---

#### 의존성 주입(Dependency Injection, DI)

<details>
<summary>의존성 주입(Dependency Injection, DI)에 대해서 말해주세요.</summary>

- 의존성 주입은 **객체 간의 의존성을 외부에서 주입해주는 기법**이다.
- 이를 통해 **느슨한 결합 코드를 작성**할 수 있으며, 테스트 용이성을 높일 수 있다.

<details>
<summary>⁉️ 스프링의 의존성 주입 방식에 대해 말해주세요.</summary>

- **생성자 주입(Constructor Injection)**: 의존성을 클래스의 생성자를 통해 주입하는 방식이다.
- **세터 주입(Setter Injection)**: 클래스의 세터 메서드를 통해 의존성을 주입하는 방식이다.
- **필드 주입(Field Injection)**: 클래스의 필드에 직접 의존성을 주입하는 방식이다.

> 생성자 주입 방식이 가장 권장되는 방법으로, 필수적인 의존성을 명시적으로 제공하며 불변성을 제공한다.

</details>

</details>

---

#### 스프링 빈(Spring Bean)

<details>
<summary>스프링 빈(Spring Bean)에 대해 말해주세요.</summary>

- 스프링 빈은 **IoC 컨테이너에 의해 인스턴스화되며, 생성 및 관리되는 객체**이다.
- 스프링 빈은 스프링 애플리케이션의 구성 요소이며, 스프링 설정 파일에 정의되거나 @Componet, @Service 등의 어노테이션으로 표시된다.

<details>
<summary>⁉️ 스프링 빈을 정의하는 방법에 대해 말해주세요.</summary>

- **스프링 빈 정의: XML 설정 방식**

```xml
<!-- 예시: 스프링 빈 설정
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans 
       http://www.springframework.org/schema/beans/spring-beans.xsd">

  <bean id="myService" class="com.example.MyService"/>
</beans> 
-->
```

- **스프링 빈 정의: 자바 기반 설정 방식**

```java

@Configuration
public class AppConfig {

	@Bean
	public MyBean myBean() {
		return new MyBean();
	}
}
```

- **스프링 빈 정의: 자바 어노테이션 설정 방식**

```java

@Component
public class MyBean {
}
```

</details>

<br>

<details>
<summary>⁉️ 스프링 빈의 생명주기에 대해 말해주세요.</summary>

- **빈 생성(Instantiation)**: 스프링 IoC 컨테이너는 빈의 정의를 바탕으로 빈 객체를 생성한다. 이 단계에서 기본 생성자가 호출된다.
- **의존성 주입(Dependency Injection)**: 빈이 생성된 후, IoC 컨테이너는 해당 빈의 의존성을 주입한다. 이 과정은 생성자, 세터, 필드 주입 등의 방식으로 이루어질 수 있다.
- **초기화(Initialization)**: 빈이 의존성을 주입받은 후, 초기화 과정이 시작된다. @PostConstruct, init-method 속성
- **사용(Usage)**: 빈이 생성되고 초기화된 후, 애플리케이션에서 사용된다. 이 시점에서 빈은 의존성을 가지고 있으며, 필요한 작업을 수행한다.
- **소멸(Destruction)**: 애플리케이션이 종료되거나 빈이 더 이상 필요하지 않을 때, 빈의 소멸 과정이 시작된다. @PreDestroy, destroy-method 속성

> IoC 컨테이너는 스프링 빈의 생명 주기인 빈 생성 -> 의존성 주입 -> 초기화 -> 사용 -> 소멸 과정을 관리하여 빈의 생명 주기를 효율적으로 처리한다.

</details>

<br>

<details>
<summary>⁉️ @Component, @Service, @Repository, @Controller 어노테이션의 차이점에 대해 말해주세요.</summary>

- **@Componet**: 일반적인 스프링 빈을 정의할 때 사용한다. 특별한 역할이 없고, 특정한 목적에 맞지 않는 일반적인 컴포넌트를 나타낸다.
- **@Service**: 서비스 계층의 빈을 정의할 때 사용한다. 비즈니스 로직이 포함된 서비스 클래스를 나타내며, 주로 데이터 처리와 관련된 로직을 수행한다.
- **@Repository**: 데이터 접근 계층의 빈을 정의할 때 사용한다. 데이터베이스와의 상호작용을 처리하는 클래스에 사용된다.
- **@Controller**: 웹 애플리케이션의 컨트롤러를 정의할 때 사용한다. HTTP 요청을 처리하고, 사용자에게 응답을 반환하는 역할을 한다. 주로 MVC 패턴에서 사용된다.

</details>

</details>

---

#### 스프링 MVC

<details>
<summary>Spring MVC에 대해 말해주세요.</summary>

- 스프링 프레임워크의 웹 애플리케이션 개발을 위한 모듈로, MVC(Model-View-Controller) 디자인 패턴을 기반으로 한다.
- 애플리케이션의 비즈니스 로직, 사용자 인터페이스, 입력 처리 등을 분리하여 개발의 효율성과 유지보수성을 보여준다.

> 웹 애플리케이션을 구조적으로 개발할 수 있도록 도와주는 프레임워크로, 클라이언트 요청을 처리하고, 비즈니스 로직과 사용자 인터페이스를 효과적으로 분리한다.

<details>
<summary>⁉️ DispatcherServlet에 대해 말해주세요.</summary>

- 스프링 MVC의 핵심 구성 요소로, 클라이언트의 요청을 처리하는 **프론트 컨트롤러** 역할을 한다.
- 다양한 핸들러, 인터셉터, 뷰 리졸버 등을 설정할 수 있고, 스프링의 IoC 컨트롤러와 통합되어 의존성 주입을 통해 객체를 관리할 수 있다.

> 클라이언트 요청을 처리하는 핵심 컴포넌트로, 요청을 수신하고 적절한 컨트롤러로 전달하며, 최종적으로 클라이언트에게 응답을 반환하는 역할을 한다.

</details>

<details>
<summary>⁉️ 스프링 MVC의 동작 과정에 대해 말해주세요.</summary>

- 클라이언트 요청을 받고, 요청을 적절한 핸들러(컨트롤러)로 전달한다.
- 요청 URL에 따라 적절한 컨트롤러를 찾아 호출한다.
- 컨트롤러는 서비스 레이어를 호출하여 비즈니스 로직을 처리한다.
- 서비스로부터 받은 데이터를 모델에 담아 뷰로 전달한다.
- 뷰를 결정하고 렌더링을 지시한다.

> DispatcherServlet -> Handler Mapping -> Bussiness Logic -> Model -> ViewResolver

</details>

</details>

---

#### Spring Boot 프레임워크

<details>
<summary>Spring Boot 프레임워크에 대해 말해주세요.</summary>

- 스프링 프레임워크의 기존 개발 방식의 문제와 한계를 극복하기 위해 다양한 기능을 제공한다.
- 많은 모듈을 추가하면 설정이 복잡해지는데, 이를 해결하기 위해 스프링 부트가 탄생하게 되었다.

<br>

- 스프링 부트는 스프링 프레임워크 위에 구축된 프로젝트로, 제품 단계의 애플리케이션 개발을 간소화한다.
- 임베디드 서버, 보안, 메트릭스, 외부화된 설정과 같은 다양한 비기능을 제공하여 개발자가 최소한의 설정으로 애플리케이션을 빠르게 구축할 수 있도록 돕는다.

> 스프링 프레임워크의 복잡성을 줄이고, 빠르고 효율적인 애플리케이션 개발을 가능하게 하는 강력한 도구이다.

<details>
<summary>⁉️ 스프링 부트를 사용하는 이유, 주요 특징에 대해서 말해주세요.</summary>

- **자동 구성, AutoConfiguration**
  - 필요한 라이브러리와 설정을 자동으로 감지하여 복잡한 설정 과정을 최소화한다.

- **스타터 의존성, Starter Dependency**
  - 다양한 기능을 쉽게 추가할 수 있도록 미리 정의된 스타터 의존성을 제공한다.

- **단독 실행, Standalone**
  - 내장된 웹 서버 Tomcat, Jetty 등을 포함하여 독립적으로 실행하고, 별도의 서버 설치 없이 JAR 파일로 실행할 수 있다.

- **프로덕션 준비, Production Ready**
  - 모니터링, 메트릭스, 설정 관리 등 프로덕션 환경에 필요한 기능을 내장해서 운영 환경에 적합한 애플리케이션을 쉽게 만들 수 있다.

- **스프링의 모든 기능 사용**
  - 스프링 프레임워크의 모든 기능을 사용할 수 있으며, 기존 스프링 생태계를 그대로 활용할 수 있다.

</details>

<br>

<details>
<summary>⁉️ 스프링 부트를 사용하는 장점에 대해 말해주세요.</summary>

- **빠른 개발**: 복잡한 설정 없이 빠르게 애플리케이션을 구축할 수 있어 개발 생산성이 높아진다.
- **유연성**: 다양한 스타터와 설정 옵션을 통해 필요한 기능만 선택적으로 사용할 수 있다.
- **모듈화**: 각 기능을 모듈화하여 관리할 수 있어 유지보수가 용이하다.
- **커뮤니티와 지원**: 스프링 생태계와 풍부한 자료와 커뮤니티 지원을 받을 수 있다.

</details>

<br>

<details>
<summary>⁉️ @SpringBootApplication 어노테이션에 대해 말해주세요.</summary>

- 스프링 부트 애플리케이션을 설정하기 위한 핵심 어노테이션으로, 세 가지 어노테이션의 조합으로 이루어져 있다.


- **@SpringBootConfiguration**: 스프링 부트 애플리케이션의 설정을 정의한다.
  - @Configuration 어노테이션을 포함하여 스프링의 설정 클래스로 작동한다.

- **@EnableAutoConfiguration**: 스프링 부트의 자동 설정 기능을 활성화한다.
  - 클래스 경로에 있는 라이브러리와 설정에 따라 스프링 애플리케이션의 구성을 자동으로 설정한다.

- **@ComponetScan**: 현재 패키지와 그 하위 패키지에서 스프링의 컴포넌트를 자동으로 검색한다.
  - 이는 @Component, @Service, @Repository, @Controller와 같은 어노테이션이 붙은 클래스를 찾아 스프링의 Application Context에 등록한다.

> 스프링 부트 프레임워크를 사용하면 기본적으로 많이 사용하는 것들을 자동으로 설정하는 어노테이션을 제공한다.

</details>

<br>

<details>
<summary>⁉️ Spring Data JPA에 대해 설명해주세요.</summary>

- 스프링 프레임워크, 데이터 액세스 계층 개발을 간소화하는 Spring Data의 한 부분이다.
- JPA(Java Persistence API)와 함께 사용해 데이터베이스와의 상호작용을 간편하게 처리하도록 도와주는 모듈이다.
- CRUD(CREATE, READ, UPDATE, DELETE) 작업을 쉽게 수행하며, ORM을 통해 데이터베이스와 자바 객체 간 변환을 자동으로 처리 및 반복 코드를 줄여준다.

</details>

<br>

<details>
<summary>⁉️ Spring Repository에 대해 설명해주세요.</summary>

- **데이터베이스와의 상호작용을 간소화**하고, 코드의 가독성을 높이며, 유지보수를 용이하게 한다.
- Repository 인터페이스를 정의하면 **스프링이 자동으로 구현체를 생성**하여, 복잡한 DAO 클래스를 작성할 필요가 없다.
- 메서드 이름 기반 쿼리를 통해 **자동으로 SQL 쿼리를 생성**하여 개발자의 생산성을 높인다.
- @Transactional 어노테이션을 사용하여 여러 데이터베이스 작업을 원자적으로 처리할 수 있다.
- JPA 외에도 MongoDB, Redis 등 다양한 데이터베이스와 데이터 소스를 지원하여 유연한 데이터 접근이 가능하다.
- 데이터베이스 관련 예외를 DataAccessException으로 변환하여 예외 처리를 간소화한다.

```java
@Repository
public interface MemberRepository extends JpaRepository<Member, Long> {
    List<Member> findByLastName(String lastName);
}
```

> Spring Repository는 데이터베이스와 상호작용하기 위한 CRUD 작업 및 쿼리 메서드를 제공하며, 데이터 액세스 기술에 대한 추상화이다.

</details>

<br>

<details>
<summary>⁉️ CrudRepository와 JpaRepository의 차이에 대해 설명해주세요.</summary>

- CrudRepository: 기본적인 CRUD(CREATE, READ, UPDATE, DELETE) 작업을 위한 메서드를 제공하는 인터페이스로 JPA에 의존하지 않는다.
- JpaRepository: CrudRepository를 상속받아 기본 CRUD 메서드를 포함하며, JPA 기반 애플리케이션에서 데이터베이스와의 상호작용을 효율적으로 처리하기 위한 인터페이스이다.

> 단순 CRUD 작업이 필요할 경우 CrudRepository를 사용하고, JPA 기능을 활용한 복잡한 데이터 처리가 필요할 경우 JpaRepository를 사용하면 좋다.

</details>

</details>

---

#### 스프링 AOP

<details>
<summary>스프링 AOP에 대해 말해주세요.</summary>

- 관점 지향 프로그래밍을 지원하여 **공통 관심사를 모듈화하여** 코드의 재사용성과 유지보수성을 향상시킨다.
- 관점 지향 프로그래밍은 **핵심 관심사와 공통 관심사를 분리**하여 프로그래밍하는 기술이다.

<details>
<summary>⁉️ 스프링 AOP에서 Advice의 종류에 대해 말해주세요.</summary>

- **@Before**: 비즈니스 로직이 실행되기 전에 실행된다.
- **@AfterReturning**: 비즈니스 로직이 정상적으로 끝난 후 결과를 받아서 실행된다.
- **@AfterThrowing**: 비즈니스 로직 실행 중 예외가 발생했을 때 실행된다.
- **@After**: 비즈니스 로직 실행 후, 성공 여부와 관계없이 항상 실행된다.
- **@Around**: 비즈니스 로직 실행 전후에 모두 실행된다.

</details>

<br>

<details>
<summary>⁉️ </summary>

- 

</details>

</details>
