### 5주차 과제 : 클래스
---
목표
+ 자바의 Class에 대해 학습하세요.

학습할 것
+ 클래스 정의하는 방법
+ 객체 만드는 방법 (new 키워드 이해하기)
+ 메소드 정의하는 방법
+ this 키워드 이해하기

---
### 클래스
+ 유사한 특징을 지닌 객체들의 속성을 묶어 놓은 집합체 이다.      
+ 하나의 클래스를 정의 하고, 그 클래스로부터 "하나의 실례를 만드는 것을 객체 또는 인스턴스를 생성한다." 라고 한다.
```java
class charactor_info {
    // 캐릭터 정보
    String name; // 캐릭터 이름
    int level; // 캐릭터 레벨
    char gender; // 캐릭터 성별
	
    // 캐릭터 기능
    void levelUp() {
    ++level; // 레벨업
    }
}
```
클래스를 만들어보았다. 여기서 `charactor_info` 은 `클래스명` 을 뜻한다.
클래스에서 사용 가능한 접근제한자로는 `public` 또는 `defualt` 가 있다.

---
### 인스턴스의 생성과 사용

```java 
public class charactor {
    public static void main(String[] args) {
        charactor_info c = new charactor_info();
		
        c.name = "홍길동"; // 캐릭터 이름 지정
        c.level = 99; // 캐릭터 레벨
        c.levelUp(); // 레벨 상승
        c.gender = 'M'; // 캐릭터 성별
		
        System.out.println("캐릭터 이름은 " + c.name + "이고, 레벨은" 
				        + c.level + "이고, 성별은 " + c.gender + "입니다.");
    }
}
```
```
결과는 캐릭터 이름은 홍길동이고, 레벨은100이고, 성별은 M입니다.    
new 연산자를 통해 Heap 영역에 데이터를 저장할 공간을 할당받는다.     
```
참조 : <https://doublesprogramming.tistory.com/69>    

---
### 메소드 정의하는 방법     

**메소드(method)**     
+ 자바에서 클래스는 멤버(member) 로 속성을 표현하는 필드(field) 와 기능을 표현하는 메소드(method) 를 가진다.     
+ 메소드(method) 란 어떠한 특정 작업을 수행하기 위한 `명령문의 집합` 이라 할 수 있다.     

**메소드(method)의 사용 목적**     
+ 클래스에서 메소드를 작성하여 사용하는 이유는 중복되는 코드의 반복적인 프로그래밍을 피하기 위함이다.     
+ 모듈화로 인해 코드의 가독성도 좋아진다.       
+ 프로그램에 문제가 생길 경우 유지보수 또한 용의하다.     
+ 메소드를 작성할 때 되도록 하나의 기능 만을 수행하도록 작성하는 것이 좋다.     

**메소드 정의**
```java
[접근제한자]반환타입 메소드이름(매개변수) {
	// 구현부
}
```
반환 타입에는 어떠한 값도 반환하지 않는다는 의미를 가진 `void`를 명시한다.       
`void`를 명시하지 않을경우 메소드 내에서 `return` 을 사용하여 호출한 메소드로 `반환` 한다.     
참조 : <http://www.tcpschool.com/java/java_methodConstructor_method>     

---
### 생성자 정의하는 방법

**생성자**
+ 자바에서 생성자 는 인스턴스 값을 원하는 값으로 초기화 할 수 있는 메소드를 제공한다.    
+ 자바에서 생성자 의 이름은 해당 클래스 명과 같아야 한다.      
+ 생성자 는 반환 타입을 void로 선언하지 않는다.    
+ 매개변수 를 통하여 값을 전달받을 수 있고, 생성자 도 하나의 메소드 이며, 오버로딩이 가능하다.     

```java
public class Test {
    private String name;
    private int age;
    
    public test() {
	// 기본 생성자
    }
    
    public test(String name, int age) {
	// 매개변수가 있는 생성자
    }
}
```
**생성자를 작성시 주의사항**
+ 반드시 클래스명과 동일 해야한다.(대/소문자 구분)     
+ 반환형 이 존재하지 않는다.    
+ 매개변수 생성자` 를 작성하게되면 기본생성자를 JVM이 자동으로 만들어주지 않는다.(기본생성자 항상 작성하는 습관 기를 것!)    


---
### this 키워드 이해하기

`this 참조 변수` 는 인스턴스가 `자기 자신` 을 참조하는 데 사용하는 변수이다.    
```java
public class User {
    private String id;
    private String pwd;
    private String name;
    private int age;
    private char gender;

public User() {
    // 기본생성자(매개변수 없는 생성)
    // 객체 생성만을 목적으로 사용된다.
    // 기본 생성자를 생략하는 경우 -> 오류? -> 노노(JVM이 자동으로 만들어줬기 때문에 항상 객체 생성이 가능했다.)

     System.out.println("User() 기본 생성자 호출");
}

// 매개변수가 있는 생성자
// 객체 생성과 동시에 전달된 값들을 매개변수로 
public User(String id, String pwd, String name) {
    this.id = id;
    this.pwd = pwd;
    this.name = name;
    }
}
```
+ 위의 예제처럼 생성자의 매개변수 이름과 인스턴스 변수의 이름이 같을 경우 this 키워드를 붙여서 구분해야 한다.    

---
`#white-study` `#live-study` `#5주차`






