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
- [6. Spring Boot 프레임워크에 대해 말해주세요.](#spring-boot-프레임워크)

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

<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans 
       http://www.springframework.org/schema/beans/spring-beans.xsd">

  <bean id="myService" class="com.example.MyService"/>
</beans>
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

-

<details>
<summary>⁉️ </summary>



</details>

<br>

<details>
<summary>⁉️ </summary>



</details>

</details>

---
