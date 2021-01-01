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

클래스란 `유사한 특징을 지닌 객체들의 속성을 묶어 놓은 집합체` 이다.      
하나의 클래스를 `정의` 하고, 그 클래스로부터 하나의 실례를 만드는 것을 `객체 또는 인스턴스를 생성한다.` 라고 한다.
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
결과는 `캐릭터 이름은 홍길동이고, 레벨은100이고, 성별은 M입니다.`    
`new 연산자`를 통해 `Heap 영역`에 데이터를 저장할 공간을 할당받는다.     
참조 : <https://doublesprogramming.tistory.com/69>    

---
### 메소드 정의하는 방법     

**메소드(method)**     
자바에서 클래스는 `멤버(member)` 로 속성을 표현하는 `필드(field)` 와 기능을 표현하는 `메소드(method)` 를 가진다.     
그중에서 `메소드(method)` 란 어떠한 특정 작업을 수행하기 위한 `명령문의 집합` 이라 할 수 있다.     

**메소드(method)의 사용 목적**     
클래스에서 메소드를 작성하여 사용하는 이유는 `중복되는 코드`의 반복적인 프로그래밍을 피하기 위함이다.     
또한, 모듈화로 인해 코드의 `가독성`도 좋아진다.       
프로그램에 문제가 생길 경우 `유지보수` 또한 용의하다.     
메소드를 작성할 때 되도록 `하나의 기능` 만을 수행하도록 작성하는 것이 좋다.     





