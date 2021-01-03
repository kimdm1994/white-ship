### 5주차 과제 : 상속
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
