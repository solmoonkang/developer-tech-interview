### 백엔드 개발 자바 기술 면접 | 신입 개발자 JPA 단골 질문

---

- [1. JPA, Hibernate, 그리고 Spring Data JPA의 차이에 대해 말해주세요.](#jpa-hibernate-그리고-spring-data-jpa의-차이)
    - [1-1. Session과 Transaction의 역할에 대해 말해주세요.]()
- [2. JPA 엔티티 생명 주기에 대해 말해주세요.](#jpa-엔티티-생명-주기)
    - [2-1. JPA 엔티티 상태 전이에 대해 말해주세요.]()
    - [2-2. JPA Persist(), Flush() 메서드에 대해 말해주세요.]()
    - [2-3. JPA EntityManager에 대해 말해주세요.]()
- [3. 영속성 컨텍스트에 대해 말해주세요.]()
    - [3-1. 영속성 컨텍스트의 생명 주기에 대해 말해주세요.]()
    - [3-2. 영속성 컨텍스트 관리 방법에 대해 말해주세요.]()
    - [3-3. 영속성 컨텍스트 엔티티 관리 방법에 대해 말해주세요.]()
- [4. 엔티티를 캐시하는 방법에 대해 말해주세요.]()
    - [4-1. 쿼리 캐시를 사용하는 방법에 대해 말해주세요.]()
    - [4-2. Hibernate에서 1차 캐시와 2차 캐시의 차이점에 대해 말해주세요.]()
    - [4-3. Dirty Checking에 대해 말해주세요.]()
    - [4-4. FetchType.LAZY로 설정했을 때 N+1 문제가 발생하는 이유에 대해 말해주세요.]()
    - [4-5. Lazy Loading과 Eager Loading의 차이에 대해 말해주세요.]()
- [5. 연관 관계를 설정하는 방법에 대해 말해주세요.]()
    - [5-1. OneToOne, OneToMany, ManyToMany 연관 관계에 대해 말해주세요.]()
    - [5-2. 테이블 간 연관 관계를 매핑하는 방법에 대해 말해주세요.]()
    - [5-3. CascadeType에 대해 말해주세요.]()
    - [5-4. orphanRemoval 옵션에 대해 말해주세요.]()
- [6. 상속, Inheritance 전략에 대해 설명해주세요.]()
- [7. JPA에서 Query Language에 대해 말해주세요.]()
    - [7-1. Named Query에 대해 말해주세요.]()
    - [7-2. Criteria API에 대해 말해주세요.]()
    - [7-3. Criteria Query를 사용하는 이유에 대해 말해주세요.]()
    - [7-4. Hibernate에서 SQL Query를 작성하는 방법에 대해 말해주세요.]()
    - [7-5. Hibernate에서 Native SQL Query를 작성하는 방법에 대해 말해주세요.]()
- [8. 트랜잭션, Transaction의 기본 동작에 대해 말해주세요.]()
    - [8-1. Isolation Level에 대해 말해주세요.]()
    - [8-1. Propagation에 대해 말해주세요.]()
    - [8-1. @Transactional 어노테이션을 사용하는 이유에 대해 말해주세요.]()
- [9. 프록시에 대해 말해주세요.]()
    - [9-1. Hibernate에서 프록시는 어떻게 생성되고 사용되는지에 대해 말해주세요.]()
- [10. 쓰기 지연 SQL 저장소에 대해 말해주세요.]()
    - [10-1. Embedded Object에 대해 말해주세요.]()

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

#### JPA 엔티티 생명 주기

<details>
<summary>JPA 엔티티 생명 주기에 대해 말해주세요.</summary>

- **비영속 상태, Transient**: 엔티티가 생성되었지만 데이터베이스에 저장되지 않고 **영속성 컨텍스트와 연결되지 않은 상태**이다.
- **영속 상태, Managed**: persist 메서드를 호출하여 엔티티가 **영속성 컨텍스트에 저장**되고 데이터베이스에 연결된 상태이다.
  - 이 상태에서는 **변경 사항이 자동으로 감지되어 데이터베이스에 반영**된다. 이 과정을 **Dirty Checking**이라고 한다.
- **준영속 상태, Detached**: detach 메서드를 호출하거나 EntityManager가 닫힐 때, **영속성 컨텍스트에서 더 이상 관리하지 않는 상태**이다.
- **삭제 상태, Removed**: remove 메서드를 호출하여 **영속성 컨텍스트에서 제거된 상태**로, 트랜잭션이 커밋될 때 데이터베이스에서 삭제된다.

<details>
<summary>⁉️ JPA 엔티티 상태 전이에 대해 말해주세요.</summary>

1. **Transient (비영속 상태) → Managed (영속 상태)**
   - persist() 메서드를 호출하여 엔티티를 영속성 컨텍스트에 저장한다.
2. **Managed (영속 상태) → Detached (준영속 상태)**
   - detach() 메서드를 호출하거나 EntityManager가 닫힐 때 엔티티가 영속성 컨텍스트에서 분리된다.
3. **Managed (영속 상태) → Removed (삭제 상태)**
   - remove() 메서드를 호출하여 엔티티를 영속성 컨텍스트에서 제거한다.
4. **Detached (준영속 상태) → Managed (영속 상태)**
   - merge() 메서드를 호출하여 준영속 상태의 엔ㅌ니티를 다시 영속성 컨텍스트에 병합한다.

</details>

<br>

<details>
<summary>⁉️ JPA Persist(), Flush() 메서드에 대해 말해주세요.</summary>

- **persit()**: 새로운 엔티티를 영속성 컨텍스트에 추가하여 영속 상태로 전이시키며, 트랜잭션 커밋 시 데이터베이스에 저장된다.
- **flush()**: 영속성 컨텍스트의 변경 사항을 즉시 데이터베이스에 반영하지만, 트랜잭션이 커밋되기 전까지는 변경 사항이 실제 저장되지 않는다.

</details>

<br>

<details>
<summary>⁉️ JPA EntityManager에 대해 말해주세요.</summary>

</details>

</details>

---
