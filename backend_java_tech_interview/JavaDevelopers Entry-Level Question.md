### 백엔드 개발 자바 기술 면접 | 신입 개발자 JAVA 단골 질문

---

- [1. 컴파일 과정을 말해주세요.](#컴파일-과정)
    - [1-1. Compiler와 Interpreter의 차이에 대해 말해주세요.]()
- [2. String, StringBuilder, StringBuffer의 차이점에 대해 말해주세요.](#string-stringbuilder-stringbuffer의-차이)
    - [2-1. Thread Safe에 대해서 말해주세요.]()
    - [2-2. Java String이 불변 객체인 이유에 대해서 말해주세요.]()
- [3. Java의 접근 제어자의 종류와 특징](#java의-접근-제어자의-종류와-특징)
- [4. OOP의 4가지 특징에 대해서 말해주세요.](#oop의-4가지-특징)
    - [4-1. 캡슐화와 은닉화의 차이에 대해서 말해주세요.]()
- [5. OOP의 5대 원칙 (SOLID)에 대해서 말해주세요.](#oop의-5대-원칙-solid)
- [6. JVM의 구조에 대해서 말해주세요.](#jvm의-구조)
- [7. 클래스, 객체, 인스턴스의 차이에 대해서 말해주세요.](#클래스-객체-인스턴스의-차이)
- [8. Interface와 Abstract Class의 차이에 대해서 말해주세요.](#interface와-abstract-class의-차이)
- [9. CheckedException과 UnCheckedException의 차이에 대해서 말해주세요.](#checkedexception과-uncheckedexception의-차이)
- [10. Call By Reference와 Call By Value의 차이에 대해서 말해주세요.](#call-by-reference와-call-by-value의-차이)
    - [10-1. Java는 어디에 해당하는지 알려주세요.]()
- [11. 오버로딩과 오버라이딩의 차이에 대해서 말해주세요.](#오버로딩과-오버라이딩의-차이)

<br>

#### 컴파일 과정

<details>
<summary>컴파일 과정을 말해주세요.</summary>

![Java 코드의 실행 과정](/image_files/JAVA/java-execution-process.png)

1. **소스 코드 작성**: 개발자가 `.java` 파일을 작성하고, 코드 작성 후 빌드 과정에 들어간다.


2. **컴파일**: Java 컴파일러의 `javac` 명령어를 사용해 소스 코드를 바이트 코드로 구성된 `.class` 파일로 변환한다.


3. **클래스 로드**: 컴파일된 `.class` 파일을 클래스 로더에 의해서 JVM 메모리 영역에 로드한다.


![JVM의 구조(클래스 로더와 실행 엔진)](/image_files/JAVA/class-loader&execution-engine.png)  

클래스 로더가 불러오는 과정은 다음과 같은 과정을 거친다.
  - **로드**: 클래스 파일을 JVM 메모리에 가져온다.
  - **검증**: 클래스가 JVM 명세를 따르는지 검사한다.
  - **준비**: 필요한 메모리를 할당한다.
  - **분석**: 심볼릭 레퍼런스를 다이렉트 레퍼런스로 변환한다.
  - **초기화**: 클래스 변수를 초기화한다.
> 클래스 로더는 계층적으로 존재하면서 상위 클래스 로더가 가져온 내용을 먼저 확인하고 찾지 못하면 하위 클래스 로더가 클래스를 로드하게 된다.


4. **실행 엔진**: JVM에 들어온 바이트 코드는 실행 엔진에 의해 JVM 내에서 기계어로 변환되어 실행된다.

JVM 실행 엔진은 인터프리터 방식과 JIT 컴파일러 방식으로 나눠지며 각 특징은 다음과 같다.
  - **인터프리터**: 바이트 코드를 하나씩 해석하고 실행한다. 초기 실행이 간단하고 빠른 반면, 전체 실행 속도는 느리다.
  - **JIT 컴파일러**: 전체 바이트 코드를 컴파일하여 바이너리 코드로 실행한다. 변환된 코드는 이후 재사용되므로 전체 실행 속도가 빠르다.
> JVM은 기본적으로 인터프리터 방식을 사용하고 내부적으로 특정 메서드가 자주 호출되면, JIT 컴파일러가 활성화되어 해당 코드를 컴파일하여 성능을 개선한다.

<details>
<summary>⁉️ Compiler와 Interpreter의 차이에 대해서 말해주세요.</summary>

- **컴파일러**: 전체 소스 코드를 한 번에 분석하여 기계어로 번역하며, 실행 가능한 실행 파일이나 바이트 코드(`.class` 파일)를 생성한다.
  - 컴파일이 완료된 후 실행 속도가 빠르지만, 초기 컴파일 시간이 필요하다.
- **인터프리터**: 소스 코드를 한 줄씩 읽어 즉시 실행하며, 별도의 실행 파일을 생성하지 않고 코드가 실행되는 동안 해석한다.
  - 각 줄마다 해석해야 하므로 실행 속도가 느리다.

> Java에서 `javac`가 컴파일러 역할을 하며, Python의 인터프리터가 이에 해당한다.

</details>

</details>

---

#### String, StringBuilder, StringBuffer의 차이

<details>
<summary>String, StringBuilder, StringBuffer의 차이점에 대해 말해주세요.</summary>

- **String 객체**: 불변(Immutable) 객체로 한 번 생성된 문자열은 변경할 수 없다. 때문에 변하지 않는 문자열을 저장할 때 적합하다.
  - 메모리 안정성 및 Thread-Safe를 제공하는 반면, 문자열을 자주 변경할 경우 성능 저하가 발생할 수 있다.

- **StringBuilder**: 가변(Mutable) 객체로 비동기 방식으로 동작한다. 문자열을 자주 변경해야 할 때 적합하다.
  - 비동기 방식이므로 처리 속도가 빠르고, 메모리 사용 효율이 좋은 반면, 멀티스레드 환경에서는 Thread-Safe하지 않다.
- **StringBuffer**: 가변(Mutable) 객체로 동기 방식으로 동작한다. 문자열을 변경할 수 있으며, 멀티스레드 환경에서 사용된다. 멀티스레드 환경에서 문자열을 변경할 때 적합하다.
  - Thread-Safe를 제공하여 동시 접근이 가능한 반면, StringBuilder보다 성능이 느리다.

> 질문의 의도는 동기와 비동기의 기준에 따라 적절한 클래스를 선택하는 것으로 보인다.

<details>
<summary>⁉️ Thread-Safe란 무엇인지 말해주세요.</summary>

- Thread-Safe는 여러 스레드가 동시에 접근할 때도 데이터의 일관성과 안정성을 보장하는 프로그래밍 기법이다.
- Thread-Safe한 코드는 여러 스레드가 동시에 실행되더라도 프로그램이 예기치 않게 동작하지 않도록 한다.
  - 동기화(synchronization), 불변 객체(immutable objects), 또는 원자적 연산(atomic)을 통해 구현된다.
- 멀티스레드 환경에서도 데이터 무결성을 유지하며 버그를 방지하는 반면, 성능 저하를 초래할 수 있으며 복잡한 동기화 로직이 필요할 수 있다.

> 동기 방식인 StringBuffer는 Thread-Safe하고, 비동기 방식인 StringBuilder는 Thread-Safe하지 않다.

</details>

<br>

<details>
<summary>⁉️ Java String이 불변 객체인 이유에 대해서 말해주세요.</summary>

- 불변 객체는 한 번 생성된 후 상태가 변경되지 않는 객체이다.

1. **메모리 안정성**: 불변 객체는 여러 스레드에서 동시에 사용될 때 안정성을 제공한다. 데이터가 변경되지 않기 때문에 스레드 간의 충돌이 없다.
2. **캐싱 효율성**: 메모리에서 동일한 값을 가진 객체를 재사용할 수 있어 메모리 효율성을 높인다. 같은 문자열 리터럴은 동일한 객체로 참조된다.
3. **안정성**: String 객체는 프로그램의 다른 부분에서 의도치 않게 변경되는 것을 방지한다. 이는 코드의 예측 가능성을 높이고 디버깅을 용이하게 한다.
4. **해시 코드 일관성**: 불변 객체는 해시 코드가 변하지 않기 때문에 해시 기반 컬렉션에서 안정적으로 사용할 수 있다.

> Java에서 String은 불변 객체로 설계되어, 메모리 안정성과 Thread-Safe를 제공하며, 해시 기반 컬렉션에서 안전하게 사용될 수 있도록 하기 위함이다.

</details>

</details>

---

#### Java의 접근 제어자의 종류와 특징

<details>
<summary>Java에서 접근 제어자의 종류와 특징에 대해 말해주세요.</summary>

</details>

---

#### OOP의 4가지 특징

<details>
<summary>OOP의 4가지 특징에 대해서 말해주세요.</summary>

</details>

---

#### OOP의 5대 원칙 (SOLID)

<details>
<summary>OOP의 5대 원칙 (SOLID)에 대해 말해주세요.</summary>

</details>

---

#### JVM의 구조

<details>
<summary>JVM의 구조에 대해서 말해주세요.</summary>

</details>

---

#### 클래스, 객체, 인스턴스의 차이

<details>
<summary>클래스, 객체, 인스턴스의 차이에 대해서 말해주세요.</summary>

</details>

---

#### Interface와 Abstract Class의 차이

<details>
<summary>Interface와 Abstract Class의 차이에 대해서 말해주세요.</summary>

</details>

---

#### CheckedException과 UnCheckedException의 차이

<details>
<summary>CheckedException과 UnCheckedException의 차이에 대해서 말해주세요.</summary>

</details>

---

#### Call By Reference와 Call By Value의 차이

<details>
<summary>Call By Reference와 Call By Value의 차이에 대해서 말해주세요.</summary>

</details>

---

#### 오버로딩과 오버라이딩의 차이

<details>
<summary>오버로딩과 오버라이딩의 차이에 대해서 말해주세요.</summary>

</details>
