### 백엔드 개발자 | 궁금했던 내용 정리

---

#### Object vs Objects

<details>
<summary>Object 클래스 vs Objects 클래스 차이점</summary>

| 구분     | **Object 클래스**                                      | **Objects 클래스**                                        |
|--------|-----------------------------------------------------|--------------------------------------------------------|
| 소속 패키지 | `java.lang.Object`                                  | `java.util.Objects`                                    |
| 역할     | 자바의 모든 클래스의 최상위 부모 클래스                              | 객체 관련 유틸리티 메서드 모음 클래스                                  |
| 주요 메서드 | `equals()`, `hashCode()`, `toString()`, `clone()` 등 | `requireNonNull()`, `isNull()`, `equals()`, `hash()` 등 |
| 상속 여부  | 모든 클래스가 암묵적으로 상속받음                                  | 상속받지 않으며 직접 사용하는 정적 유틸 클래스                             |
| 특징     | 자바 클래스 설계의 기반이 되는 존재                                | NULL 체크 및 가독성 향상 목적의 도우미 클래스                           |

**🔷 Object 클래스**

- 자바의 모든 클래스는 ***Object*** 클래스를 암묵적으로 상속한다.

```java
public class Person {
	// 실제로는 내부적으로 extends Object가 생략되어 있음
}
```

**🔷 Objects 클래스**

- ***java.util.Objects***는 객체 유틸리티 메서드를 제공하는 헬퍼 클래스이며, 모든 메서드는 ***static***이다.

```java
import java.util.Objects;

public class Example {
	public Example(String name) {
		this.name = Objects.requireNonNull(name, "이름은 null일 수 없습니다.");
	}
}
```

</details>

---
