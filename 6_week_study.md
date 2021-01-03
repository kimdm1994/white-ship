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
`결과 : 부모와 자식의 나이를 덧셈한 결과 30`
