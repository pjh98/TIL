# 🕑자바 기본

---

<details>
    <summary><h3>자바 메모리 구조와 static</h3></summary>

* 메서드 영역(Method Area) : 메서드 영역은 프로그램을 실행하는데 필요한 공통 데이터를 관리한다. 이 영역은 프로그램의 모든 영역에서 공유한다.
  * 클래스 정보 : 클래스의 실행 코드(바이트 코드), 필드, 메서드와 생성자 코드 등 모든 실행 코드가 존재한다.
    * static 영역 : static 변수들을 보관한다.
    * 멤버 변수(필드)의 종류
      * 인스턴스 변수 : static이 붙지 않은 멤버 변수
      * 클래스 변수 : static이 붙은 멤버 변수, 정적 변수, static 변수 등으로 부르기도 한다.
  * 런타임 상수 풀 : 프로그램을 실행하는데 필요한 공통 리터럴 상수를 보관한다.
  <br></br>

* 스택 영역(Stack Area) : 자바 실행 시, 각 쓰레드별로 하나의 실행 스택이 생성된다. 따라서 쓰레드 수 만큼 스택 영역이 생성된다. 각 스택 프레임은 지역 변수, 중간 연산 결과, 메서드 호출 정보 등을 포함한다.
  * 스택 프레임 : 메서드를 호출할 때마다 하나의 스택 프레임이 쌓이고, 메서드가 종료되면 해당 스택 프레임이 제거된다.
  <br></br>

* 힙 영역(Heap Area) : 객체(인스턴스)와 배열이 생성되는 영역이다. 가비지 컬렉션(GC)이 이루어지는 주요 영역이며, 더 이상 참조되지 않는 객체는 GC에 의해 제거된다.
<br></br>

* **정적 변수 접근 법**
  * 정적 변수의 경우 인스턴스를 통한 접근은 추천하지 않는다. 코드를 읽을 때 마치 인스턴스 변수에 접근하는것 처럼 오해할 수 있기 때문이다.
    정적 변수는 클래스에서 공용으로 관리하기 때문에 클래스를 통해서 접근하는 것이 더 명확하다. 따라서 정적 변수에 접근할 때는 클래스를 통해서 접근하자.
  <br></br>
* **정적 메서드 사용법**
  * static 메서드는 static 만 사용할 수 있다.
    * 클래스 내부의 기능을 사용할 때, 정적 메서드는 인스턴스 변수나 인스턴스 메서드를 사용할 수 없다.
  * 반대로 모든 곳에서 static을 호출할 수 있다.
    * 정적 메서드는 공용 기능이다. 따라서 접근 제어자만 허락한다면 클래스를 통해 모든 곳에서 static을 호출할 수 있다.
</details>

---

<details>
    <summary><h3>final</h3></summary>

* 생성자를 사용해서 final 필드를 초기화 하는 경우, 각 인스턴스마다 final 필드에 다른 값을 할당할 수 있다. 물론 final을 사용했기 때문에 생성 이후에 이 값을 변경하는것은 불가능하다.

```java
//Field 클래스는 선언 되어있다고 가정
Field field1 = new Field();
Field field2 = new Field();
Field field3 = new Field();
```

* final 필드를 필드에서 초기화 하는 경우, 모든 인스턴스가 같은 값을 사용하기 때문에 결과적으로 메모리를 낭비하게 된다.(물론 JVM에 따라서 내부 최적화를 시도할 수 있다.)
또 메모리 낭비를 떠나서 같은 값이 계속 생성되는 것은 개발자가 보기에 명확한 중복이다. 이럴 때 사용하면 좋은것이 바로 static 영역이다.
  * static final
    * static 영역은 단 하나만 존재하는 영역이다. 필드에 final + 필드 초기화를 사용하는 경우 static을 붙여서 사용하면 중복과 메모리 비효율 문제를 모두 해결할 수 있어서 효과적이다.

* final은 정말 유용한 제약이다. 만약 특정 변수의 값을 할당한 이후 변경하지 않아야 한다면 final을 사용하자. 만약 어디선가 실수로 값을 변경한다면 컴파일러가 문제를 찾아줄 것이다.
</details>

---

<details>
  <summary><h3>상속(Inheritance)</h3></summary>

* 자바는 다이아몬드 문제와 클래스 계층 구조가 복잡해지는 문제를 피하기 위해 다중 상속이 아닌 단일 상속만 지원한다.
* 상속과 메모리 구조
  * 상속 관계의 객체를 생성하면 그 내부에는 부모와 자식이 모두 생성된다.
  * 상속 관계의 객체를 호출할 때, 대상 타입을 정해야한다. 이때 호출자의 타입을 통해 대상 타입을 찾는다.
  * 현재 타입에서 기능을 찾지 못하면 상위 부모 타입으로 기능을 찾아서 실행한다. 기능을 찾지 못하면 컴파일 오류가 발생한다.
* 상속과 메서드 오버라이딩
  * 부모에게서 상속 받은 기능을 자식이 재정의하는것 => 메서드 오버라이딩
  * 상위 클래스의 메서드를 오버라이딩할때 메서드 위에 @Override 애노테이션을 붙여줘야 컴파일러가 오버라이딩 조건을 만족시키지 않으면 컴파일 에러를 발생시켜서 실수로 오버라이딩을 못하는 경우를 방지할 수 있다.
* super
  * 부모와 자식의 필드명이 같거나 메서드가 오버라이딩 되어있으면 자식에서 부모의 필드나 메서드를 호출할 수 없다. 이때 super 키워드를 사용하면 부모를 참조할 수 있다. super는 말 그대로 부모 클래스에 대한 참조를 나타낸다.
  * 상속 관계를 사용하면 자식 클래스의 생성자에서 부모 클래스의 생성자를 반드시 호출해야 한다.(기본 생성자인 경우 super() 생략 가능)
</details>

---

<details>
  <summary><h3>다형성(Polymorphism)</h3></summary>

* 다형적 참조
  * 부모 타입의 변수가 자식 인스턴스를 참조하는것
  * 상속관계는 부모 방향으로 찾아 올라갈 수 있지만 자식 방향으로 찾아 내려갈 수 없다. 자식 인스턴스를 호출하고 싶을때 *캐스팅*이 필요하다.
* 캐스팅
  * 다운캐스팅(downcasting) : 자식 타입으로 변경
    * ```
      ex) Parent가 부모 클래스, Child가 Parent를 상속받는 자식 클래스일때,
      Child child = (Child) poly;
      child.childMethod();
      ```
    * 일시적 다운캐스팅
    ```
    Parent poly = new Child();
    ((Child)poly).childMethod();
    ```
    * 다운태스팅 주의점
      * 인스턴스에 존재하지 않는 하위 타입으로 캐스팅해서 `ClassCastException`이라는 런타임 예외를 발생 시킬 수 있다.
  * 업캐스팅(upcasting) : 부모 타입으로 변경
    * ```
      Child child = new Child();
      Parent parent1 = (Parent) child;
      Parent parent2 = child; //업캐스팅은 생략 권장
      ```
</details>

---

<details>
  <summary><h3>추상 클래스</h3></summary>

* 추상 클래스
  * 상속을 목적으로 부모 클래스는 제공하는, 기존 클래스에서 인스턴스를 생성하지 못하는 제약이 추가된 클래스
* 추상 메서드
  * 추상 메서드가 하나라도 있는 클래스는 추상 클래스로 선언해야 한다.
  * 추상 메서드는 상속 받는 자식 클래스가 반드시 오버라이딩 해서 사용해야 한다.
* 순수 추상 클래스 => 인터페이스(자바에서 편리하게 순수 추상 클래스를 사용할 수 있게 인터페이스 기능 지원)
  * ```
    순수 추상 클래스
    public abstract class AbstractAnimal{
      public abstract void sound();
      public abstract void move();
    }
    ```
    ```
    인터페이스
    public interface InterfaceAnimal{
      void sound();
      void move();
    }
    ```
  * 인터페이스를 사용해야 하는 이유
    * 제약 : 순수 추상 클래스의 경우 미래에 누군가 실행한 가능한 메서드를 끼워 넣을 수 있다. 이렇게 되면 추가된 기능을 자식 클래스에서 구현하지
    않을 수도 있고, 또 더는 순수 추상 클래스가 아니게 된다. 인터페이스는 모든 메서드가 추상 메서드이다. 따라서 이런 문제를 원천 차단할 수 있다.
    * 다중 구현 : 자바에서 클래스 상속은 부모를 하나만 지정할 수 있다. 반면에 인터페이스는 부모를 여러명 두는 다중 구현이 가능하다.
    >자바8에 등장한 default 메서드, 자바9에 등장한 인터페이스의 private 메서드를 사용하면 인터페이스도 메서드를 구현할 수 있다.  
하지만 이것은 예외적으로 아주 특별한 경우에만 사용해야 한다.
</details>