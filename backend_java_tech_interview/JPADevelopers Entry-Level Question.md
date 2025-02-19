### 백엔드 개발 자바 기술 면접 | 신입 개발자 JPA 단골 질문

---

- [1. JPA, Hibernate, 그리고 Spring Data JPA의 차이에 대해 말해주세요.](#jpa-hibernate-그리고-spring-data-jpa의-차이)
    - [1-1. Session과 Transaction의 역할에 대해 말해주세요.]()
- [2. JPA 엔티티 생명 주기에 대해 말해주세요.](#jpa-엔티티-생명-주기)
    - [2-1. JPA 엔티티 상태 전이에 대해 말해주세요.]()
    - [2-2. JPA Persist(), Flush() 메서드에 대해 말해주세요.]()
    - [2-3. EntityManager에 대해 말해주세요.]()
- [3. 영속성 컨텍스트에 대해 말해주세요.](#영속성-컨텍스트-persistence-context)
- [4. 1차 캐시와 2차 캐시의 차이에 대해 말해주세요.](#1차-캐시-first-level-cachel1-cache와-2차-캐시-second-level-cachel2-cache)
    - [4-1. Hibernate 쿼리 캐시에 대해 말해주세요.]()
    - [4-2. 더티 체킹, Dirty Checking에 대해 말해주세요.]()
    - [4-3. 지연 로딩, Lazy Loading과 즉시 로딩, Eager Loading의 차이에 대해 말해주세요.]()
    - [4-4. 지연 로딩 시 N+1 문제가 발생하는 이유에 대해 말해주세요.]()
- [5. JPA에서 연관관계 설정 시 일대일, 일대다, 다대일, 다대다의 차이에 대해 말해주세요.](#jpa-연관관계-종류)
    - [5-1. 일대다 관계를 사용할 때 주의해야 할 점에 대해 말해주세요.](#)
    - [5-2. 다대일 관계에서 중간 매핑 테이블을 사용하는 이유에 대해 말해주세요.]()
    - [5-3. CascadeType 설정은 어떻게 하며, 어떤 상황에서 사용하는지에 대해 말해주세요.]()
    - [5-4. orphanRemoval 옵션으 무엇이고, 어떤 경우에 사용하는지에 대해 말해주세요.]()
- [6. 상속, Inheritance 전략에 대해 말해주세요.]()
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
<summary>⁉️ EntityManager에 대해 말해주세요.</summary>

- 엔티티의 **생명 주기를 관리**하고 데이터베이스와의 상호작용을 수행하는 주요 **인터페이스**이다.
- EntityManager 객체는 엔티티를 영속성 컨텍스트에 저장하고, 쿼리를 실행하며, 트랜잭션을 관리하는 역할을 한다.

</details>

</details>

---

#### 영속성 컨텍스트, Persistence Context

<details>
<summary>영속성 컨텍스트에 대해 말해주세요.</summary>

- 엔티티를 **메모리에 저장 및 관리**하며, 데이터베이스와의 상호작용을 최적화한다.
- EntityManager는 하나의 영속성 컨텍스트와 연결되어 있으며, EntityManager가 사용될 때까지 유지된다.
- 데이터베이스와의 실제 연결 없이 엔티티의 상태를 관리하는 **가상의 저장소 역할**을 하며, 엔티티의 상태 변화는 데이터베이스에 자동으로 반영된다.

</details>

---

#### 1차 캐시, First-Level Cache(L1 Cache)와 2차 캐시, Second-Level Cache(L2 Cache)

<details>
<summary>1차 캐시와 2차 캐시의 차이에 대해 말해주세요.</summary>

- **1차 캐시**: 각 EntityManager에 의해 관리되는 캐시로, 영속성 컨텍스트 내에서 엔티티의 상태를 저장한다.
    - EntityManager 인스턴스에 국한되어 있으며, 해당 인스턴스가 열려 있는 동안만 유효하다.
    - 변경을 자동으로 감지하는 Dirty Checking으로 데이터베이스에 반영하며, 메모리에 저장되어 데이터베이스 접근을 줄여 성능 향상과 빠른 속도를 제공한다.

- **2차 캐시**: 애플리케이션 전체에서 공유되는 캐시로, 여러 EntityManager 인스턴스에서 사용 가능하다.
    - EntityManager가 종료되어도 캐시는 유지되며, 설정에 따라 지속적으로 존재할 수 있다.
    - 동시성 극대화를 위해 데이터의 복사본을 반환하며, 데이터 일관성 관리를 위해 캐시 무효화 정책이나 TTL을 설정할 수 있다.

<details>
<summary>⁉️ Hibernate 쿼리 캐시에 대해 말해주세요.</summary>

- **엔티티 캐시, Entity Cache**: 자주 조회되는 엔티티의 상태를 메모리에 저장해 데이터베이스 접근을 줄인다.
- **컬렉션 캐시, Collection Cache**: 특정 엔티티와 관련된 컬렉션의 데이터를 캐시하여, 해당 엔티티를 조회할 때 관련된 컬렉션을 신속히 가져올 수 있도록 한다.
- **쿼리 캐시, Query Cache**: 동일한 쿼리를 반복적으로 실행할 때, 데이터베이스에 접근하지 않고 캐시된 결과를 반환하여 성능을 향상시킨다.

<br>

**쿼리 캐시 사용 방법**

1. Hibernate 설정: application.properties에서 쿼리 캐시를 활성화한다.

```properties
spring.jpa.properties.hibernate.cache.use_second_level_cache=true
spring.jpa.properties.hibernate.cache.region.factory_class=org.hibernate.cache.ehcache.EhCacheRegionFactory
spring.jpa.properties.hibernate.cache.use_query_cache=true
```

2. 쿼리 캐시 사용: 쿼리를 실행할 때 setHint를 사용하여 쿼리 캐시를 사용하도록 설정한다.

```java
entityManager.createQuery("SELECT M FROM Member M")
  .

setHint("org.hibernate.cacheable",true) // 쿼리 캐시 사용
  .

getResultList();
```

<br>

**Spring Data JPA에서 쿼리 캐시 사용 방법**

1. Spring Data JPA 설정: application.properties에서 쿼리 캐시를 활성화한다.

```properties
spring.jpa.properties.hibernate.cache.use_second_level_cache=true
spring.jpa.properties.hibernate.cache.region.factory_class=org.hibernate.cache.ehcache.EhCacheRegionFactory
spring.jpa.properties.hibernate.cache.use_query_cache=true
```

2. 쿼리 캐시 사용: Spring Data JPA의 @Query 어노테이션을 사용하여 쿼리 캐시를 설정한다.

- Hibernate의 쿼리 캐시를 활용한다면 @QueryHints를 사용하여 활성화한다.

```java
public interface MemberRepository extends Repository<Member, Long> {

	@QueryHints(value = {
		@QueryHint(name = "org.hibernate.cacheable", value = "true"),
		@QueryHint(name = "org.hibernate.cacheRegion", value = "member-by-lastname") // cache-region 값 설정
	})
	Page<Member> findByLastname(String lastname, Pageable pageable);
}
```

- Spring의 캐시 기능을 통해 메서드 결과를 캐시하고 싶다면 @Cacheable을 사용하여 활성화한다.

```java

@Query(value = "SELECT M FROM Member M", nativeQuery = false)
@org.springframework.cache.annotation.Cacheable
	// 캐시 사용 설정
List<Member> findAllMembers();
```

</details>

<br>

<details>
<summary>⁉️ 더티 체킹, Dirty Checking에 대해 말해주세요.</summary>

- JPA는 엔티티의 상태를 영속성 컨텍스트 내에서 관리한다. 엔티티가 영속 상태에 있을 때, JPA는 해당 엔티티의 필드 값을 감시한다.
- 엔티티의 필드 값이 변경되면, JPA는 이를 감지하여 해당 엔티티가 **더티, Dirty** 상태임을 인식한다.
- 더티 체킹은 주로 트랜잭션이 커밋될 때 이루어지며, 변경된 내용을 데이터베이스에 자동으로 반영한다.

```java
Member member = entityManager.find(Member.class, 1);
member.

setName("NewName");   // 필드 값 변경

entityManager.

getTransaction().

commit();   // 변경된 내용이 데이터베이스에 반영된다.
```

> JPA가 변경을 감지하기 위해서는 필드 값을 직접 수정하거나 setter 메서드를 사용해야 한다. 그렇지 않을 경우 JPA는 변경 사항을 인식하지 못한다.

</details>

<br>

<details>
<summary>⁉️ 지연 로딩, Lazy Loading과 즉시 로딩, Eager Loading의 차이에 대해 말해주세요.</summary>

- **지연 로딩, Lazy Loading**: 필요할 때만 데이터를 로드하여 성능과 메모리를 최적화하지만, N+1 문제와 같은 단점이 있을 수 있다.
- **즉시 로딩, Eager Loading**: 모든 연관 데이터를 즉시 로드하여 데이터 접근이 용이하지만, 초기 로딩 시간과 메모리 사용량이 증가할 수 있다.

</details>

<br>

<details>
<summary>⁉️ 지연 로딩 시 N+1 문제가 발생하는 이유에 대해 말해주세요.</summary>

- 연관된 엔티티를 실제 필요 시까지 로드하지 않는 방식으로 부모 엔티티 조회 후, 자식 엔티티에 접근할 때마다 추가적인 쿼리가 실행된다.
- 이를 해결하기 위해 _JOIN FETCH_, _Batch Fetching_, *FetchType.EAGER*를 사용하는 방법이 있다.

</details>

</details>

---

#### JPA 연관관계 종류

<details>
<summary>JPA에서 연관관계 설정 시 일대일, 일대다, 다대일, 다대다의 차이에 대해 말해주세요.</summary>

- **일대일(1:1)**: 하나의 엔티티가 다른 엔티티와 일대일 관계를 가지는 경우이다.
- **일대다(1:N)**: 하나의 엔티티가 여러 엔티티와 관계를 가지는 경우이다.
- **다대일(N:1)**: 여러 엔티티가 하나의 엔티티와 관계를 가지는 경우이다.
- **다대다(N:M)**: 여러 엔티티가 서로 관계를 가지는 경우이다.

> 데이터베이스를 기준으로 다중성을 결정하며, 다(N) 쪽이 외래키를 가지고 있다.

<details>
<summary>⁉️ 일대다 관계를 사용할 때 주의해야 할 점에 대해 말해주세요.</summary>

</details>

<br>

<details>
<summary>⁉️ 다대일 관계에서 중간 매핑 테이블을 사용하는 이유에 대해 말해주세요.</summary>

</details>

<br>

<details>
<summary>⁉️ CascadeType 설정은 어떻게 하며, 어떤 상황에서 사용하는지에 대해 말해주세요.</summary>

</details>

<br>

<details>
<summary>⁉️ orphanRemoval 옵션으 무엇이고, 어떤 경우에 사용하는지에 대해 말해주세요.</summary>

</details>

</details>

---
