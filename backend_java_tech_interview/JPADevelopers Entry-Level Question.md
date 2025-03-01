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
    - [5-4. orphanRemoval 옵션은 무엇이고, 어떤 경우에 사용하는지에 대해 말해주세요.]()
- [6. JPA 상속 관계 매핑 전략에 대해 말해주세요.](#jpa-상속-관계-매핑)
    - [6-1. @MappedSuperclass이 무엇이고, 사용하는 이유에 대해 말해주세요.]()
- [7. JPQL(Java Persistence Query Language)에 대해 말해주세요.](#객체-지향-쿼리-언어)
    - [7-1. @NamedQuery와 @Query의 차이에 대해 말해주세요.]()
    - [7-2. Criteria API에 대해 말해주세요.]()
    - [7-3. Hibernate에서 SQL Query를 작성하는 방법에 대해 말해주세요.]()
    - [7-4. Hibernate에서 Native SQL Query를 작성하는 방법에 대해 말해주세요.]()
- [8. 트랜잭션, Transaction에 대해 말해주세요.](#트랜잭션-transaction)
    - [8-1. 트랜잭션의 ACID 성질에 대해 말해주세요.]()
    - [8-2. @Transactional에 대해 말해주세요.]()
    - [8-3. 트랜잭션 격리 수준(Isolation Levels)에 대해 말해주세요.]()
    - [8-4. 트랜잭션 전파 방식(Propagation)에 대해 말해주세요.]()
    - [8-5. 비관적 락 & 낙관적 락에 대해 말해주세요.]()
- [9. JPA 프록시 객체에 대해 말해주세요.](#jpa-프록시-객체)
    - [9-1. 프록시 객체를 언제 사용하는지에 대해 말해주세요.]()
    - [9-2. 프록시 객체를 사용할 때 주의할 점에 대해 말해주세요.]()
    - [9-3. 프록시 객체를 사용할 때 성능상의 이점에 대해 말해주세요.]()
    - [9-4. 프록시 객체가 어떻게 생성되는지에 대해 말해주세요.]()
- [10. 쓰기 지연 SQL 저장소에 대해 말해주세요.](#sql-실행-최적화)
    - [10-1. 배치 처리에 대해 말해주세요.]()
    - [10-2. Embedded Object에 대해 말해주세요.]()

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

- 일대다(1:N) 관계에서 일(1) 쪽의 수정만 했지만, 다(N) 쪽의 수정이 생겨 쿼리가 발생하게 된다.
- 일대다(1:N) 단방향 연관관계 매핑이 필요한 경우, **다대일(N:1) 양방향 연관관계 매핑**이 추후 유지보수가 더 수월하다.

</details>

<br>

<details>
<summary>⁉️ 다대일 관계에서 중간 매핑 테이블을 사용하는 이유에 대해 말해주세요.</summary>

- 다대다(N:M) 관계는 중간 테이블이 숨겨져 있어 복잡한 조인 쿼리가 발생할 수 있다.
- 자동 생성된 중간 테이블은 외래 키 외에 다른 정보들도 저장하므로 문제가 발생할 확률이 높다.

> 다대다(N:M) 관계는 일대다(1:N) 혹은 다대일(N:1) 관계로 풀어서 중간 테이블을 엔티티로 만드는 것이 유연한 변경이 도움이 된다.

</details>

<br>

<details>
<summary>⁉️ CascadeType 설정은 어떻게 하며, 어떤 상황에서 사용하는지에 대해 말해주세요.</summary>

- **CASCADE 영속성 전이**는 **부모 엔티티의 상태 변화가 자식 엔티티에 전파**되는 기능이다.

```java

@Entity
public class Child {
	@Id
	@GeneratedValue(strategy = GenerationType.IDENTITY)
	private Long id;

	@ManyToOne
	@JoinColumn(name = "parent_id") // 외래 키 설정
	private Parent parent;

	// 기타 필드, 생성자, getter/setter 등
}

@Entity
public class Parent {
	@Id
	@GeneratedValue(strategy = GenerationType.IDENTITY)
	private Long id;

	@OneToMany(mappedBy = "parent", cascade = CascadeType.ALL)
	private List<Child> children = new ArrayList<>();

	// 기타 필드, 생성자, getter/setter 등
}
```

- CascadeType의 종류로는 **PERSIST**, **MERGE**, **REMOVE**, **REFRESH**, **DETACH**, **ALL**이 있다.

</details>

<br>

<details>
<summary>⁉️ orphanRemoval 옵션은 무엇이고, 어떤 경우에 사용하는지에 대해 말해주세요.</summary>

- **부모 엔티티와의 관계가 끊어진 자식 엔티티를 자동으로 삭제**하는 JPA 기능이다.
- 관계를 정의할 때 `orphanRemoval = true`로 설정하여 사용하며, 주로 자식 엔티티가 더 이상 필요하지 않을 때 데이터 무결성 유지를 위해 사용한다.

</details>

</details>

---

#### JPA 상속 관계 매핑

<details>
<summary>JPA 상속 관계 매핑 전략에 대해 말해주세요.</summary>

- **조인 전략**: 부모 클래스와 자식 클래스 각각에 테이블을 생성한다.
    - 부모 클래스의 테이블과 자식 클래스의 테이블을 조인하여 데이터를 조회한다.
    - @Inheritance(strategy = InheritanceType.JOINED)를 부모 클래스에 사용한다.

- **단일 테이블 전략**: 모든 클래스의 데이터를 하나의 테이블에 저장한다.
    - @Inheritance(strategy = InheritanceType.SINGLE_TABLE)를 부모 클래스에 사용한다.
    - @DiscriminatorColumn과 @DiscriminatorValue를 사용하여 각 서브타입을 구별한다.

- **구현 클래스별 테이블 전략**: 각 서브타입마다 별도의 테이블을 생성한다.
    - @Inheritance(strategy = InheritanceType.TABLE_PER_CLASS)를 부모 클래스에 사용한다.

<details>
<summary>⁉️ @MappedSuperclass이 무엇이고, 사용하는 이유에 대해 말해주세요.</summary>

- JPA에서 부모 클래스가 테이블로 매핑되지 않도록 하면서, 자식 클래스가 부모 클래스의 필드를 상속받을 수 있게 한다.
- 공통 속성을 여러 엔티티에 적용하고 싶을 때 유용하다.

</details>

</details>

---

#### 객체 지향 쿼리 언어

<details>
<summary>JPQL(Java Persistence Query Language)에 대해 말해주세요.</summary>

- JPA에서 제공하는 객체 지향 쿼리 언어로, SQL과 유사하지만 데이터베이스 테이블이 아닌 엔티티 객체를 기반으로 쿼리를 작성한다.

**JPQL 특징**

- **객체 지향적**: 엔티티와 그 속성을 사용하여 쿼리를 구성한다.
- **데이터베이스 독립성**: JPA 구현체에 따라 다르게 해석될 수 있어, 특정 데이터베이스에 종속되지 않아 이식성이 높다.
- **동적 쿼리**: 동적 쿼리를 작성할 수 있는 기능을 제공하며, 조건에 따라 쿼리를 변경할 수 있다.

```java
public class AlbumRepository {

	@PersistenceContext
	private EntityManager entityManager;

	public List<Album> findAlbumsByArtist(String artist) {
		String jpql = "SELECT a FROM Album a WHERE a.artist = :artist";
		TypedQuery<Album> query = entityManager.createQuery(jpql, Album.class);
		query.setParameter("artist", artist);
		return query.getResultList();
	}
}
```

> JPQL은 객체 지향적인 데이터 접근을 가능하게 하며, 데이터베이스 구조에 의존하지 않고 엔티티를 중심으로 쿼리를 작성할 수 있다.

<details>
<summary>⁉️ @NamedQuery와 @Query의 차이에 대해 말해주세요.</summary>

- **NamedQuery**: 미리 정의된 JPQL 쿼리로, 엔티티 클래스 레벨에서 @NamedQuery를 사용하여 정의한다.

```java
@NamedQuery(name = "Member.findByName", query = "SELECT m FROM Member m WHERE m.name = :name")
```

- Query: Spring Data JPA에서 제공하는 어노테이션으로, 메서드에 직접 JPQL 또는 SQL 쿼리를 정의할 수 있다.

```java
@Query("SELECT m FROM Member m WHERE m.name = :name")
Member findByName(@Param("name") String name);
```

> @NamedQuery는 반복적이고 성능이 중요할 때, @Query는 복잡한 쿼리나 동적으로 작성할 때 유용하다.

</details>

<br>

<details>
<summary>⁉️ Criteria API에 대해 말해주세요.</summary>

- JPQL을 자바 코드로 작성하도록 도와주는 빌더 클래스 API로, 타입-세이프하고 동적 쿼리를 작성할 수 있다.
  - 타입-세이프로 인해 컴파일 안정성을 제공하며, 컴파일 타임에 오류를 검출할 수 있다.
  - 코드가 복잡하고 장황하여 직관적이지 못해 이해하기 힘들다는 단점이 있다.

</details>

<br>

<details>
<summary>⁉️ Hibernate에서 SQL Query를 작성하는 방법에 대해 말해주세요.</summary>

- HQL, Hibernate Query Language
  - 객체 지향 쿼리 언어로, 엔티티 객체를 기반으로 쿼리를 작성한다. SQL과 유사하지만, 데이터베이스 테이블이 아닌 엔티티 클래스를 대상으로 한다.

```java
String HQL = "FROM Member WHERE name = :name";
Query query = session.createQuery(HQL);
query.setParameter("name", "John");
List<Member> results = query.list();
```

> HQL은 JPQL의 기능을 포함하고 있으며, Hibernate에서만 사용된다.

- Criteria API
  - 동적 쿼리를 작성할 수 있는 방법으로, 타입 안정성을 제공하여 객체 지향적으로 쿼리를 구성할 수 있다.

```java
CriteriaBuilder criteriaBuilder = session.getCriteriaBuilder();
CriteriaQuery<Member> criteriaQuery = criteriaBuilder.createQuery(Member.class);
Root<Member> memberRoot = criteriaQuery.from(Member.class);
criteriaQuery.select(memberRoot).where(criteriaBuilder.equal(memberRoot.get("name"), "John"));
List<Member> results = session.createQuery(criteriaQuery).getResultList();
```
</details>

<br>

<details>
<summary>⁉️ Hibernate에서 Native SQL Query를 사용하는 방법에 대해 말해주세요.</summary>

- 데이터베이스의 원시 SQL 쿼리를 직접 작성하는 방법으로, Hibernate에서는 createSQLQuery 메서드를 사용하여 Native SQL을 실행할 수 있다.

```java
String SQL = "SELECT * FROM members WHERE name = :name";
SQLQuery query = session.createSQLQuery(SQL);
query.setParameter("name", "John");
query.addEntity(Member.class); // 결과를 Member 엔티티로 매핑
List<Member> results = query.list();
```

</details>

</details>

---

#### 트랜잭션, Transaction

<details>
<summary>트랜잭션, Transaction에 대해 말해주세요.</summary>

- JPA에서 트랜잭션은 **데이터베이스의 상태를 변화시키는 작업의 단위**를 의미한다.
- 즉, 데이터베이스에서 수행되는 일련의 작업으로, 모두 성공적으로 완료되거나 모두 실패해야 하는 단위이다.

<details>
<summary>⁉️ 트랜잭션의 ACID 성질에 대해 말해주세요.</summary>

- **원자성, Atomicity**: 트랜잭션 내의 모든 작업이 완전히 수행되거나 전혀 수행되지 않아야 한다.
  - 즉, 트랜잭션의 일부분이 실패하면 전체 트랜잭션이 롤백되어 이전 상태로 되돌아간다.

- **일관성, Consistency**: 트랜잭션이 성공적으로 완료되면 데이터베이스는 일관된 상태로 유지되어야 한다.
  - 즉, 트랜잭션이 완료된 후에도 데이터의 무결성이 보장되어야 한다.

- **격리성, Isolation**: 동시에 실행되는 트랜잭션이 서로 간섭하지 않도록 보장한다.
  - 각 트랜잭션은 다른 트랜잭션에 영향을 주지 않고 독립적으로 실행되어야 한다.

- **지속성, Durability**: 트랜잭션이 성공적으로 완료되면 결과는 영구적으로 저장되어야 하며, 시스템 장애가 발생해도 유지되어야 한다.

</details>

<br>

<details>
<summary>⁉️ @Transactional에 대해 말해주세요.</summary>

- JPA에서는 EntityManager를 통해 트랜잭션을 관리하며, 스프링에서는 트랜잭션 관리를 더 쉽게 하기 위해 @Transactional 어노테이션을 제공한다.
- 메서드 또는 클래스 레벨에 적용하여 해당 메서드 또는 클래스의 모든 작업을 하나의 트랜잭션으로 묶는다.
- 기본적으로 메서드가 성공적으로 완료되면 커밋하고, 예외가 발생하면 롤백한다.

```java
@Service
public class BankService {

    @Transactional
    public void transferFunds(Long sourceAccountId, Long targetAccountId, Double amount) {
        withdrawFromAccount(sourceAccountId, amount);
        depositToAccount(targetAccountId, amount);
    }

    private void withdrawFromAccount(Long accountId, Double amount) {
        // 계좌 잔액 확인 후 출근하는 서비스 로직
    }

    private void depositToAccount(Long accountId, Double amount) {
        // 계좌에 금액을 추가하는 서비스 로직
    }
}
```

> 트랜잭션은 데이터의 일관성을 보장하기 위한 최소 단위로, 스프링에서는 @Transactional을 사용해 편리하게 관리할 수 있다.

</details>

<br>

<details>
<summary>⁉️ 트랜잭션 격리 수준(Isolation Levels)에 대해 말해주세요.</summary>

- 격리 수준은 동시에 실행되는 트랜잭션 간의 간섭을 방지하기 위한 설정이다.


- **READ_UNCOMMITTED**: 다른 트랜잭션의 변경 사항(커밋되지 않은 데이터)도 읽을 수 있다. 단, Dirty Read 발생이 가능하다.
- **READ_COMMITTED(DEFAULT)**: 커밋된 데이터만 읽을 수 있다. Dirty Read 방지가 가능하지만, Non-Repeatable Read 발생이 가능하다.
- **REPEATABLE_READ**: 한 트랜잭션 내에서 동일한 데이터를 여러 번 읽어도 값이 변하지 않는다. Non-Repeatable Read 방지가 가능하지만, Phantom Read 발생이 가능하다.
- **SERIALIZABLE**: 가장 엄격한 수준으로 트랜잭션을 순차적으로 실행한다. Phantom Read 방지가 가능하지만, 동시성이 낮아지고 성능이 저하된다.

</details>

<br>

<details>
<summary>⁉️ 트랜잭션 전파 방식(Propagation)에 대해 말해주세요.</summary>

- 전파 수준은 기존 트랜잭션이 있는 경우 새로운 트랜잭션을 어떻게 실행할지 결정하는 설정이다.


- **REQUIRED(DEFAULT)**: 기존 트랜잭션이 있으면 합쳐서 사용하고, 없으면 새로 생성한다.
- **REQUIRES_NEW**: 기존 트랜잭션을 무시하고 항상 새 트랜잭션을 생성한다.
- **NESTED**: 기존 트랜잭션 안에서 중첩 트랜잭션을 실행한다. 독립적인 롤백이 가능하다.
- **SUPPORTED**: 기존 트랜잭션이 있으면 사용하고, 없으면 트랜잭션 없이 실행된다.
- **NOT_SUPPORTED**: 트랜잭션을 지원하지 않는다. 기존 트랜잭션이 있으면 일시 중단된다.
- **MANDATORY**: 반드시 기존 트랜잭션 내에서 실행되며, 없으면 예외가 발생한다.
- **NEVER**: 기존 트랜잭션이 있으면 예외가 발생하고, 없으면 트랜잭션 없이 실행된다.

</details>

<br>

<details>
<summary>⁉️ 비관적 락 & 낙관적 락에 대해 말해주세요.</summary>

- 비관적 락: 데이터 충돌 가능성이 높다고 보고 미리 데이터에 잠금을 걸어 다른 트랜잭션의 접근을 제한하는 방식이다.

> 비관적 락은 높은 동시성 환경에서 데이터 일관성을 강하게 보장하지만 성능 저하의 위험이 있다.

- 낙관적 락: 데이터 충돌 가능성이 드물다 보고 업데이트 시점에 버전 정보를 통해 충돌을 감지하는 방식이다.

> 낙관적 락은 성능 오버헤드가 적은 대신 충돌 발생 시 예외 처리가 필요하다.

</details>

</details>

---

#### JPA 프록시 객체

<details>
<summary>JPA 프록시 객체에 대해 말해주세요.</summary>

- 프록시는 실제 엔티티를 감싸는 가짜 객체로, 데이터베이스 조회를 지연시키기 위해 사용된다.
- Hibernate가 프록시 클래스를 동적으로 생성하여 필드에 접근할 때만 실제 데이터를 조회한다.

<details>
<summary>⁉️ 프록시 객체를 언제 사용하는지에 대해 말해주세요.</summary>

- 연관된 엔티티를 지연 로딩할 때 사용된다.
- @OneToMany, @ManyToOne 등의 관계에서 FetchType.LAZY로 설정하면 Hibernate가 프록시 객체를 생성한다.

> 즉시 로딩, EAGER: 엔티티 조회 시 연관된 모든 엔티티를 JOIN을 사용해 한 번에 조회한다.
 
> 지연 로딩, LAZY: 엔티티 조회 시 프록시 객체를 생성하고, 필요할 때 데이터베이스를 조회한다.

</details>

<br>

<details>
<summary>⁉️ 프록시 객체를 사용할 때 주의할 점에 대해 말해주세요.</summary>

- 프록시 객체는 실제 엔티티가 아니라서 instanceof 검사 시 주의해야 한다.
- 프록시 객체를 사용할 때는 영속성 컨텍스트가 유지되어야 한다. 그렇지 않으면 LazyInitializationException이 발생한다.

> 지연 로딩된 프록시 객체를 사용할 때, 영속성 컨텍스트가 종료된 상태에서 데이터에 접근하면 발생하는 예외이다.

</details>

<br>

<details>
<summary>⁉️ 프록시 객체를 사용할 때 성능상의 이점에 대해 말해주세요.</summary>

- 연관된 엔티티를 즉시 로딩(EAGER)하면 불필요한 데이터까지 조회하게 된다.
- 프록시 객체를 활용하면 정말 필요한 데이터만 로딩할 수 있어서 성능 최적화가 가능하다.

</details>

<br>

<details>
<summary>⁉️ 프록시 객체가 어떻게 생성되는지에 대해 말해주세요.</summary>

- Hibernate가 CGLIB 또는 ByteBuddy 같은 라이브러리를 이용하여 동적으로 생성한다.
- 실제 엔티티 클래스를 상속받은 프록시 클래스를 만들어서 데이터를 조회할 때만 데이터베이스에 접근하도록 처리한다.

</details>

</details>

---

#### SQL 실행 최적화

<details>
<summary>쓰기 지연 SQL 저장소에 대해 말해주세요.</summary>

- 엔티티의 변경 사항을 즉시 데이터베이스에 반영하지 않고, 영속성 컨텍스트에 저장해두었다가 한 번에 데이터베이스로 전송하는 전략이다.
- 데이터베이스 접근 횟수를 줄여 성능 및 효율성을 향상시키지만, 메모리 관리와 데이터 일관성에 주의가 필요하다.

<details>
<summary>⁉️ 배치 처리에 대해 말해주세요.</summary>

- 여러 SQL DML 작업(INSERT, UPDATE, DELETE)을 한 번에 묶어서 처리하는 기법이다.
- 네트워크 왕복 횟수를 줄여 성능을 향상시키며, 대량 처리 시 유용하지만 트랜잭션 관리와 오류 처리에 주의가 필요하다.

</details>

<br>

<details>
<summary>⁉️ Embedded Object에 대해 말해주세요.</summary>

- 엔티티 내에 포함되어 같은 테이블에 저장되는 값 타입 객체이다.
- @Embeddable과 @Embedded를 사용하여 필드를 그룹화하고 재사용성을 높이며, 별도의 식별자(PK)가 없고 엔티티에 종속된다.

</details>

</details>

---
