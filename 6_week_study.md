### 6주차 과제 : 상속
---
목표
+ 자바의 상속에 대해 학습하세요.

학습할 것
+ 자바 상속의 특징
+ super 키워드
+ 메소드 오버라이딩
+ 다이나믹 메소드 디스패치 (Dynamic Method Dispatch)
+ 추상 클래스
+ final 키워드
+ Object 클래스
---
### 자바 상속의 특징

**상속이란?**         
`상속(inheritance)이란` 기존 클래스에 기능을 추가하거나 재정의하여 새로운 클래스를 정의하는 것이다.        
이때 기존에 정의한 클래스를 `상위 클래스(super class)`, 또는 `부모 클래스(parents class)`라고 한다.

**상속의 장점**
1. 기존에 작성한 클래스를 `재정의`하여 다시 활용할 수 있다.        
2. 자식 클래스 설계 시 중복되는 멤버를 미리 부모 클래스에 작성하면, 자식 클래스는 해당 멤버를 작성하지 않아도 된다.       
3. 클래스 간의 `계층적 관계`를 구성함으로써 `다형성`의 문법적 토대를 마련한다.

**상속 문법**
```java
class 자식클래스 명 extends 부모클래스명 { ... }
```

**예제**
```java
class Parent {
    private int a = 10; // public 또는 protected 사용
    public int parentAge = 10;
}

class Child extends Parent {
    private int childAge = 20;
	
    void add() {
        System.out.println(parentAge + childAge);
    }
}

public class inheritTest {

    public static void main(String[] args) {
        Child child = new Child();
        System.out.print("부모와 자식의 나이를 덧셈한 결과 ");
        child.add();
    }
}
```
**실행결과**
```java
부모와 자식의 나이를 덧셈한 결과 30
```
+ Child 클래스가 Parent 클래스를 상속받았기 때문에 parentAge 값을 사용하여 출력할 수 있었다.
+ 자식 클래스에는 부모 클래스의 필드와 메소드만이 상속되며, 생성자와 초기화 블록은 상속되지 않는다.
+ 부모 클래스의 접근제한자가 private이나 default로 설정된 멤버는 자식 클래스에서 상속받지만 접근 할수 없다.    
+ 자바에서 클래스는 단일 상속만 가능하다.       

---
### super 키워드     
super 키워드는 부모 클래스로부터 상속받은 필드나 메소드를 자식 클래스에서 참조하는데 사용하는 참조 변수이다.      
부모 클래스의 멤버와 자식 클래스의 이름이 같을 경우 super 키워드로 구분할 수 있다.       

**1. super**
```java
class Parent {
    int a = 10;
}

class Child extends Parent {
    int a = 20;
    void print() {
        System.out.println(a);
        System.out.println(this.a);
        System.out.println(super.a);
    }
}


public class inheritTest {

public static void main(String[] args) {
    Child child = new Child();

    child.print();
    }
}
```
**실행결과**
```java
20
20
10
```
자식 클래스의 필드를 재정의 해주더라도 `super`로 참조하게 될 경우 부모의 값을 가져온다.

---
**2. super()**
+ super() 메소드는 부모 클래스의 생성자를 호출할 때 사용된다.
+ 부모 클래스의 멤버를 초기화하기 위해서는 자식 클래스의 생성자에서 부모클래스의 생성자까지 호출해야한다.
+ super()를 호출함으로써 부모 클래스의 멤버를 초기화할 수 있다.      
```java
class Parent {
    int a;

    Parent (int n) {
        a = n;
    }
}

class Child extends Parent {
    int b;

    Child() {
        super(40);
        b = 20;
    }

    void display() {
        System.out.println(a);
        System.out.println(b);
    }
}

public class inheritTest {

    public static void main(String[] args) {
        Child child = new Child();

        child.display();
    }
}
```
**실행결과**
```java
40
20
```
+ 자바 컴파일러는 자동으로 첫 줄에 super(); 구문을 삽입한다.
참조 : <http://www.tcpschool.com/java/java_inheritance_super>            

---
### 메소드 오버라이딩
**메소드 오버라이딩**
+ 자식 클래스가 상속 받은 부모 클래스의 메소드를 재정의 하는 것이다.
+ 자식 객체를 통해 자식 메소드가 우선권을 가진다.
**오버라이딩 성립 조건**
+ 부모 클래스의 메소드와 메소드명이 동일
+ 매개변수 개수, 자료형, 순서가 동일
+ 반환형 동일
+ 부모 메소드의 접근제한자 보다 범위가 같거나 커야한다.(public > protected > default > private)

**예제**
```java
class Parent {

    void display() {
        System.out.println("부모 클래스의 display() 메소드입니다.");
    }
}

class Child extends Parent {
    void display() {
        System.out.println("자식 클래스의 display() 메소드입니다.");
    }
}

public class inheritTest {
    public static void main(String[] args) {
        Parent pa = new Parent();
        pa.display();
        Child ch = new Child();
        ch.display();
        Parent pc = new Child();
        pc.display();
    }
}
```
**실행결과**
```java
부모 클래스의 display() 메소드입니다.
자식 클래스의 display() 메소드입니다.
자식 클래스의 display() 메소드입니다.
```

**오버로딩(Overloading)과 오버라이딩(Overriding)**
+ 오버로딩과 오버라이딩은 혼동하기가 쉽다. 하지만 개념을 확실히 해야한다.
+ 오버로딩(Overloading)은 새로운 매소드를 정의하는 것이다.
+ 오버라이딩(Overriding)은 상속받은 기존의 메소드를 재정의하는 것이다.

---

### 다이나믹 메소드 디스패치 (Dynamic Method Dispatch)         
메소드 디스패치(Method Dispatch)란 어떤 메소드를 호출할지 결정하여 실행하는것을 말한다.

**정적 디스패치(Static Dispatch)**
+ 컴파일 시점에서, 어떤 메소드를 호출할 것이지 알고있는 경우이다.
+ 상위(Super) 클래스가 존재하더라도, 서브 클래스를 레퍼런스로 선언하고 서브 클래스의 인스턴스를 만든것도 해당된다.
```java
public class Test {
    public static void main(String[] arg) {
        Dispatch dispatch = new Dispatch();
        System.out.println(dispatch.method());
    }
}

class Dispatch{
    public String method(){
        return "hello dispatch";
    }
}
```

**동적 디스패치(Dynamic Dispatch)**
+ 인터페이스 타입으로 메소드(Method)를 호출한다
+ 런타임(Runtime)시에 메소드(Method)의 호출이 결정이 된다.
+ 런타임시에 호출 객체를 알 수 있기에 어떤 객체에 메소드를 호출해야하는지 드러나지 않는다.
```java
public class Test {
    public static void main(String[] arg) {
        Dispatchable dispatch = new Dispatch();
        System.out.println(dispatch.method());
    }
}

class Dispatch implements Dispatchable {
    public String method(){
        return "hello dispatch";
    }
}

interface Dispatchable{
    String method();
}
```
출처: <https://multifrontgarden.tistory.com/133>
**더블 디스패치(Double Dispatch)**      
+ Dispatch가 연속으로 이루어지는 것을 말한다

---
### 추상 클래스
**추상 메소드(abstract method)**
+ 추상 메소드란 자식 클래스에서 반드시 오버라이딩해야만 사용할 수 있다.
+ 사용 목적으로는 추상 메소드가 포함된 클래스를 자식 클래스가 반드시 추상 메소드를 구현하도록 하기 위함이다.
+ {...} 몸통부가 구현되지 않은 상태
+ 미완성된 추상메소드가 있다는 이야기는 이 클래스 또한 미완성상태이다. 즉, 해당 클래스로 객체를 생성할 수 없다.
+ 자식 클래스에서 무조건 재정의 해줘야한다. 재정의를 해주지않으면 에러가 발생한다.    

**문법**
```java
[접근제한자] abstract void 메소드명();
```
**추상 클래스(abstract class)**
+ 하나 이상의 추상 메소드를 포함하는 클래스를 추상클래스(abstract class)라고 한다.
+ 다형성을 가지는 메소드의 집합을 정의할 수 있도록 해준다.
+ 추상 메소드를 선헌해 놓으면, 반드시 재정의해줘야한다.

**문법**
```java
[접근제한자] abstract class 클래스이름 {
    
    [접근제한자] abstract 반환타입 메소드이름();
}
```
+ 추상 클래스는 동작이 정의되어 있지 않은 추상 메소드를 포함하고 있어서, 인스턴스를 생성할 수 없다.
+ 추상 클래스는 먼저 상속을 통해 자식클래스를 만들고, 만든 자식 클래스에서        
추상 클래스의 메소드를 오버라이딩하고 나서 자식 클래스의 인스턴스를 생성 할 수 있다.

---
### final 키워드       
final 키워드를 사용할 수 있는 대상은 `클래스(Class), 메소드(Method), 멤버변수(Field)`가 있다.        

**final class**     
부모 클래스를 상속한 자식 클래스를 만들어보자       
```java
public class Child extends Parent {
    private int age = 50;
}
```
부모 클래스에 final 키워드를 사용하여 작성해보자        
```java
public final class Parent {
    public int height = 170;
}
```
+ 부모 클래스를 상속하여 만든 자식 클래스에서 에러가 발생하게 된다.

**final method**       
부모 클래스에 final method를 작성하고 테스트해보자
```java
public class Parent {
    protected final String methodTest() {
		
    }
}
```
```java
public class Child extends Parent {
    protected String methodTest() {

}
```
+ Remove 'final' ... 에러가 발생할 것이다.        
+ 이처럼 final 키워드가 포함되어있는 메소드는 오버라이딩을 할 수 없다.        

**final Field**      
```java
public class FinalFieldClass {
    final int ROWS = 10; // 상수 정의, 이때 초깃값(10)을 반드시 설정

    void f() {
        int[] intArray = new int[ROWS]; // 상수 활용
        ROWS = 30; // 컴파일 오류. final 필드 값은 상수으므로 변경할 수 없다.
    }
}
```
출처 : <https://gmlwjd9405.github.io/2018/08/06/java-final.html>     
+ final 상수 필드를 정의할 때 반드시 초깃값을 지정해야 한다.
+ 상수 필드는 한 번 정의되면 값을 변경할 수 없다.
+ fianl 키워드만을 사용하여 상수를 만들면 FinalFieldClass의 객체들만 사용할 수 있는 상수가 된다.      

프로그램 전체에서 공유하여 사용할 수 있는 상수
+ final 키워드 + static (public static final)
+ public static final double PI = 3.14159265358979323846;


---
### Object 
