### 백엔드 개발 자바 기술 면접 | 신입 개발자 JPA 단골 질문

---

- [1. JPA, Hibernate, 그리고 Spring Data JPA의 차이에 대해 말해주세요.](#jpa-hibernate-그리고-spring-data-jpa의-차이)
    - [1-1. Hibernate에서 Session과 Transaction의 역할에 대해 말해주세요.]()
- [2. ]()

<br>

#### JPA, Hibernate, 그리고 Spring Data JPA의 차이

<details>
<summary>JPA, Hibernate, 그리고 Spring Data JPA의 차이에 대해 말해주세요.</summary>

- **JPA, Java Persistence API**: 데이터베이스와의 상호작용을 위해 **EntityManager를 통해 구현되는 인터페이스**로, ORM의 표준이다.
- **Hibernate**: **JPA를 구현한 라이브러리**로, 많은 기능과 성능 최적화를 제공한다. 다른 JPA 구현체로 쉽게 전환이 가능하다.
- **Spring Data JPA**: JPA를 기반으로 Repository 인터페이스를 통해 **메서드 이름에 맞는 쿼리를 자동으로 생성**해주는 편리한 기능을 제공한다.

<details>
<summary>⁉️ Hibernate에서 Session과 Transaction의 역할에 대해 말해주세요.</summary>

- **Session**: Hibernate와 데이터베이스 간의 연경을 관리한다.
  - **CRUD 작업**: 엔티티를 저장, 조회, 업데이트, 삭제하는 작업을 수행한다.
  - **1차 캐시**: 엔티티 객체를 1차 캐시에 저장하여 동일한 세션 내에서 동일한 객체에 대한 중복 조회를 방지한다.
  - **쿼리 실행**: HQL이나 Criteria API를 사용하여 쿼리를 실행하고 결과를 반환한다.


- **Transaction**: 데이터베이스 작업의 원자성을 보장한다.
  - **원자성 보장**: 여러 데이터베이스 작업이 모두 성공하거나 모두 실패하게 함으로써 데이터의 일관성을 유지한다.
  - **커밋 / 롤백**: 트랜잭션을 사용하여 작업을 커밋(확인)하거나 롤백(취소)할 수 있다.
  - **동시성 제어**: 트랜잭션을 통해 데이터베이스의 동시성 문제를 관리한다.

> Session은 Hibernate와 데이터베이스 간의 상호작용을 관리하는 반면, Transaction은 데이터베이스 작업의 원자성과 일관성을 보장하는 역할을 한다.

</details>

</details>

---

#### 

<details>
<summary></summary>

<details>
<summary>⁉️ </summary>

</details>

</details>

---
