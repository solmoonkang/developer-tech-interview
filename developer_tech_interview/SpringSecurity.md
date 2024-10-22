## Spring Security란?

---

Spring Security는 Spring 기반의 애플리케이션 보안(인증 및 인가)을 담당하는 스프링 프레임워크이다.

Spring Security는 인증과 권한에 대한 부분을 Filter의 흐름에 따라 처리한다.

- Filter는 DispatcherServlet으로 가기 전에 적용되어 가장 먼저 URL 요청을 받는다.
- 반면, Interceptor는 Dispatcher와 Controller 사이에 위치하여 적용 시기의 차이가 있다.

## Spring Security를 사용하는 이유

---

Java 개발자들이 보안 기능을 추가할 때 Spring Security를 사용하는 이유는 Spring Security가 Spring 생태계에서 보안에 필요한 기능들을 제공하기 때문이다.

Spring Security는 개발 구조가 Spring 프레임워크 안에서 활용하기 적합한 구조로 설계되어 있어, 보안 기능을 추가할 때 활용하기 좋다.

프레임워크를 사용하지 않고 코드를 직접 작성할 경우 Spring에서 추구하는 IoC / DI 패턴과 같은 확장 패턴을 염두해서 인증 및 인가 부분을 직접 개발하기 쉽지 않다.

- Spring Security에서는 이와 같은 기능들을 제공해주기 때문에 개발 작업의 효율을 높일 수 있다.

### Authentication(인증) & Authorization(인가)

- **Authentication, 인증**: 해당 사용자가 본인이 맞는지를 확인하는 절차
- **Authorization, 인가**: 인증된 사용자가 요청한 자원에 접근 가능한지를 결정하는 절차

![Authentication & Authorization](/image_files/Security/authentication&authorization.png)

Spring Security는 기본적으로 인증 절차를 거친 후에 인가 절차를 진행하게 되며, 인가 과정에서 해당 리소스에 대한 접근 권한이 있는지 확인을 하게 된다.

Spring Security에서는 이러한 인증 및 인가를 위해 Principal을 아이디로, Credential을 비밀번호로 사용하는 Credential 기반의 인증 방식을 사용한다.

- **Principal, 접근 주체**: 보호받는 리소스에 접근하는 대상
- **Credential, 비밀번호**: 리소스에 접근하는 대상의 비밀번호

## Spring Security Filter란?

---

SpringMVC에서는 요청을 가장 먼저 받는 곳은 DispatcherServlet이다.

- 그리고 DispatcherServlet이 요청을 받기 전에는 다양한 필터가 있을 수 있다.
- 필터가 하는 역할은 클라이언트와 자원 사이에서 요청과 응답을 이용한 다양한 처리에 목적이 있다.

### Security Filter Chain

Spring Security는 다양한 기능을 가진 필터들을 10개 이상을 기본적으로 제공한다.

- 이렇게 제공되는 필터들을 Security Filter Chain이라고 한다.

![SecurityFilterChain](/image_files/Security/security-filter-chain.png)

## PasswordEncoder란?

---

Spring Security에서는 비밀번호를 안전하게 저장할 수 있도록 비밀번호의 단방향 암호화를 지원한다.

이는 PasswordEncoder 인터페이스와 구현체들이다.

- **encode( )**: 비밀번호를 암호화한다.
- **matchers( )**: 암호화된 비밀번호와 암호화되지 않은 비밀번호가 일치하는지 비교한다.
- **upgradeEncoding( )**: 인코딩된 암호화를 다시 한 번 인코딩할 때 사용한다.

### BCryptPasswordEncoder이란?

BCrypt는 암호화를 할 때 해시 알고리즘인 SHA-256을 사용한다.

- 해시 알고리즘의 특징은 암호화는 가능하나 복호화는 불가능하다.
- 때문에, 데이터베이스에 암호화되어 있는 값을 해독할 수 없다.

예를 들어, 어느 사이트에서 비밀번호를 잊었을 경우 비밀번호를 찾기 위해 재설정이 필요한 곳이 있다.

해당 이유는 BCrypt의 특성으로 복호화가 불가능하기 때문에 기존 값을 대체할 값을 넣어야 한다.

### PasswordEncoder에서 제공하는 구현 클래스

Spring Security는 여러 인코딩 알고리즘을 제공하며, PasswordEncoder 클래스는 다음과 같다.

- StandardPasswordEncoder: SHA-256을 이용해 암호를 해시한다.
- Pbkdf2PasswordEncoder: PBKDF2를 이용한다.
- BCryptPasswordEncoder: BCrypt 강력 해싱 함수로 암호를 인코딩한다.
- NoOpPasswordEncoder: 암호를 인코딩하지 않고 일반 텍스트로 유지한다.
- SCryptPasswordEncoder: SCrypt 해싱 함수로 암호를 인코딩한다.
- DelegationPasswordEncoder: 여러 인코딩 알고리즘을 사용할 수 있도록 한다.

## Spring Security 주요 모듈

---

### Authentication

```java
public interface Authentication extends Principal, Serializable {
    Collection<? extends GrantedAuthority> getAuthorities();

    Object getCredentials();

    Object getDetails();

    Object getPrincipal();

    boolean isAuthenticated();

    void setAuthenticated(boolean isAuthenticated) throws IllegalArgumentException;
}
```

Authentication은 현재 접근하는 주체의 정보와 권한을 담는 인터페이스이다.

### SecurityContext

Authentication을 보관하는 역할을 하며, SecurityContext를 통해 Authentication 객체를 꺼낼 수 있다.

### SecurityContextHolder

보안 주체의 세부 정보를 포함하여 응용 프로그램의 현재 보안 컨텍스트에 대한 세부 정보가 저장된다.

쉽게 이해하기 위해 3가지 모듈의 연관 관계를 살펴보자. 예를 들어, 사용자가 로그인을 통해 인증을 한다.

1. 해당 사용자가 인증에 성공하면 principal과 credential 정보를 Authentication에 담는다.
2. Spring Security에서 Authentication을 SpringContext에 보관한다.
3. SpringContext를 SecurityContextHolder에 담아서 보관한다.

### UserDetails

인증에 성공하면 생성된 UserDetails 객체는 Authentication 객체를 구현한 UsernamePasswordAuthenticationToken을 생성하기 위해 사용된다.

```java
public interface UserDetails extends Serializable {
    Collection<? extends GrantedAuthority> getAuthorities();

    String getPassword();

    String getUsername();

    default boolean isAccountNonExpired() {
        return true;
    }

    default boolean isAccountNonLocked() {
        return true;
    }

    default boolean isCredentialsNonExpired() {
        return true;
    }

    default boolean isEnabled() {
        return true;
    }
}
```

### UserDetailsService

UserDetailsService는 UserDetails 객체를 반환하는 하나의 메서드만을 가지고 있는데, 일반적으로 이를 implements한 클래스에서 UserRepository를 주입받아 데이터베이스와 연결하여 처리한다.

- 즉, 이곳에서 데이터베이스에 저장된 사용자 정보를 조회한다.

```java
public interface UserDetailsService {
    UserDetails loadUserByUsername(String username) throws UsernameNotFoundException;
}
```

### UsernamePasswordAuthenticationToken

Authentication을 implements한 AbstractAuthenticationToken의 하위 클래스로,

- User의 ID가 Principal 역할을 하고,
- Passsword가 Credential의 역할을 한다.

UsernamePasswordAuthenticationToken의 첫 번째 생성자는 인증 전의 객체를 생성하고,

두 번째는 인증이 완료된 객체를 생성한다.

```java
public class UsernamePasswordAuthenticationToken extends AbstractAuthenticationToken {
    private static final long serialVersionUID = 620L;
    private final Object principal;
    private Object credentials;

    public UsernamePasswordAuthenticationToken(Object principal, Object credentials) {
        super((Collection)null);
        this.principal = principal;
        this.credentials = credentials;
        this.setAuthenticated(false);
    }

    public UsernamePasswordAuthenticationToken(Object principal, Object credentials, Collection<? extends GrantedAuthority> authorities) {
        super(authorities);
        this.principal = principal;
        this.credentials = credentials;
        super.setAuthenticated(true);
    }
}
```

### AuthenticationManager

인증에 대한 부분은 AuthenticationManager를 통해 처리하게 된다.

- 실질적으로는 AuthenticationManager에 등록된 AuthenticationProvider에 의해 처리된다.
- 이를 implements 한 것이 ProviderManager이다.

인증에 성공하면 두 번째 생성자를 이용해 객체를 생성하여 SecurityContext에 저장한다.

### AuthenticationProvider

AuthenticationProvider에서는 실제 인증에 대한 부분을 처리하는데, 인증 전의 Authentication 객체를 받아서 인증이 완료된 객체를 반환하는 역할을 한다.

## Spring Security 처리 과정

---

![SpringSecurity Architecture](/image_files/Security/security-architecture.png)

### 1. 클라이언트가 로그인을 시도한다.

### 2-a. AuthenticationFilter에서 인증을 처리한다.

ServletFilter에 의해서 SecurityFilter로 Security 작업이 위임되고,

여러 SecurityFilter 중에서 UsernamePasswordAuthenticationFilter에서 인증을 처리한다.

### 2-b. UsernameAuthenticationToken을 발급한다.

AuthenticationFilter는 HttpServletRequest에서 아이디와 비밀번호를 추출하여 UsernameAuthenticationToken을 발급한다.

### 3. AuthenticationManager에게 인증 객체를 전달한다.

AuthenticationFilter는 AuthenticationManager에게 인증 객체를 전달한다.

AuthenticationManager는 인증을 담당하여 2번 과정에서 발급한 토큰이 올바른 유저인지 확인한다.

### 4. 인증을 위해 AuthenticationProvider에게 인증 객체를 전달한다.

### 5. 전달받은 인증 객체의 정보를 UserDetailsService에 전달한다.

AuthenticationProvider는 전달받은 인증 객체의 정보를 UserDetailsService에 넘겨준다.

### 6. UserDetails 구현 객체를 생성한다.

UserDetailsService는 전달받은 사용자 정보를 통해 데이터베이스에서 알맞은 사용자를 조회한다.

- 이를 기반으로 UserDetails를 구현한 객체를 반환한다.
- UserDetailsService의 loadUserByUsername 메서드는 UserDetails 객체를 반환한다.

### 7. UserDetails 객체를 AuthenticationProvider에 전달한다.

### 8. ProviderManager에게 권한을 담은 검증된 인증 객체를 전달한다.

AuthenticationProvider는 전달받은 UserDetails를 인증하여 성공하면 ProviderManager에게 권한을 담은 검증된 인증 객체를 전달한다.

### 9. 검증된 인증 객체를 AuthenticationFilter에게 전달한다.

ProviderManager가 AuthenticationFilter에 인증된 객체를 전달한다.

### 10. 검증된 인증 객체를 SecurityContextHolder의 SecurityContext에 저장한다.

AuthenticationFilter가 UserDetails 정보를 SecurityContextHolder에 저장한다.

### 참고 자료
[Spring Security란?](https://mangkyu.tistory.com/76)
[Spring Security 처리 과정 및 구현 예제](https://mangkyu.tistory.com/77)
[Spring Security 개념과 처리 과정](https://hello-judy-world.tistory.com/216)
[Spring Security를 이용한 로그인 구현](https://velog.io/@dh1010a/Spring-Spring-Security%EB%A5%BC-%EC%9D%B4%EC%9A%A9%ED%95%9C-%EB%A1%9C%EA%B7%B8%EC%9D%B8-%EA%B5%AC%ED%98%84-%EC%8A%A4%ED%94%84%EB%A7%81%EB%B6%80%ED%8A%B8-3.X-%EB%B2%84%EC%A0%84-3)
