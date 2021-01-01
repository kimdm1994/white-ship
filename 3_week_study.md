### 3주차 과제 : 연산자
---
목표
+ 자바가 제공하는 다양한 연산자를 학습하세요.

학습할 것
+ 산술 연산자
+ 비트 연산자
+ 관계 연산자
+ 논리 연산자
+ instanceof
+ assignment(=) operator
+ 화살표(->) 연산자
+ 3항 연산자
+ 연산자 우선 순위
+ (optical) Java 13. switch 연산자

---

<table border="1px">
    <th colspan="5">연산자</th>
    <tr>
        <td>구분</td>
        <td>연산자</td>
        <td>기능</td>
    </tr>
    <tr>
        <td rowspan="4">단항연산자</td>
        <td>!(논리부정)</td>
        <td>논리값을 부정, True는 false, False는 true 반환</td>
    </tr>
    <tr>
        <td>~(비트 부정)</td>
        <td>해당 데이터의 각 비트는 변환한다.</td>
    </tr>
    <tr>
        <td>+, -(부호)</td>
        <td>부호를 변경하는 연산자</td>
    </tr>
    <tr>
        <td>++, --(증감연산자)</td>
        <td>값을 증감하는 연산자</td>
    </tr>
    <tr>
        <td>산술 연산자</td>
        <td>*, /, +, -	</td>
        <td>사칙연산을 하기 위한 연산자</td>
    </tr>
    <tr>
        <td>시프트 연산자</td>
        <td><<, >>, >>></td>
        <td>주어진 비트만큼 이동하는 연산자</td>
    </tr>
    <tr>
        <td>비교 연산자</td>
        <td><, <=, >, >=, ==, !=</td>
        <td>참과 거짓을 판단하는 연산자</td>
    </tr>
    <tr>
        <td>논리 연산자</td>
        <td>AND, OR, XOR</td>
        <td>논리값을 판단하는 연산자</td>
    </tr>
    <tr>
        <td>조건 연산자</td>
        <td>?, :</td>
        <td>조건식의 결과에 따라 수행하는 값을 결정하는 연산자</td>
    </tr>
    <tr>
        <td>대입 연산자</td>
        <td>=, +=, -=, *=, /=, %=, <<=, >>=, >>>=, &=, ^=	</td>
        <td>변수에 값을 대입하는 연산자</td>
    </tr>
</table>

---

#### 산술 연산자
```
산술 연산자는 기본적인 사칙연산을 수행한다.
문자열 끼리의 덧셈연산을 하게되면 각 문자열이 하나의 문자열로 이어진다.
```
```java
public static void main(String) {
    int result = 1 + 2; // 1 + 2 = 3
    result = result - 1; // 3 - 1 = 2
    result = result * 2; // 2 * 2 = 4
    result = result / 2; // 4 / 2 = 2
    result = result % 7; // 2 % 7 = 2
    
    String str1 = "Merry ";
    String str2 = "Cristmass";
    String str3 = str1 + str2; // Merry Cristmass
}
```

---

#### 비트 연산자

```
비트 논리 연산자는 대상이 boolean 타입일 경우에는 일반 논리 연산자로 활용되지만   
대상이 정수일 경우에는 비트 논리연산자로 활용된다.   
각 정수값을 비트단위로 나열하여 자릿수 연산을 한다.   
자릿수의 연산은 독립적이며, 다른 자릿수에 영향을 주지 않는다.
```
```java
public static void matin(String[] args) {
    int a = 1; // 0000 0001
    int b = 2; // 0000 0010
    
    int result1 = a & b; // 0
    int result2 = a | b; // 3
    int result3 = a ^ b; // 3
    int result4 = ~a; // -2
}
```

<table border="1">
   <tr>
       <th colspan="3">& (AND)</th>
   </tr>
   <tr>
       <th>입력1</th>
       <th>입력2</th>
       <th>출력</th>
   </tr>
   <tr>
       <td>0</td>
       <td>0</td>
       <td>0</td>
   </tr>
   <tr>
       <td>0</td>
       <td>1</td>
       <td>0</td>
   </tr>
   <tr>
       <td>1</td>
       <td>0</td>
       <td>0</td>
   </tr>
   <tr>
       <td>1</td>
       <td>1</td>
       <td>1</td>
   </tr>
</table>

<table border="1">
   <tr>
       <th colspan="3">| (OR)</th>
   </tr>
   <tr>
       <th>입력1</th>
       <th>입력2</th>
       <th>출력</th>
   </tr>
   <tr>
       <td>0</td>
       <td>0</td>
       <td>0</td>
   </tr>
   <tr>
       <td>0</td>
       <td>1</td>
       <td>1</td>
   </tr>
   <tr>
       <td>1</td>
       <td>0</td>
       <td>1</td>
   </tr>
   <tr>
       <td>1</td>
       <td>1</td>
       <td>1</td>
   </tr>
</table>

<table border="1">
   <tr>
       <th colspan="3">^ (XOR)</th>
   </tr>
   <tr>
       <th>입력1</th>
       <th>입력2</th>
       <th>출력</th>
   </tr>
   <tr>
       <td>0</td>
       <td>0</td>
       <td>0</td>
   </tr>
   <tr>
       <td>0</td>
       <td>1</td>
       <td>1</td>
   </tr>
   <tr>
       <td>1</td>
       <td>0</td>
       <td>1</td>
   </tr>
   <tr>
       <td>1</td>
       <td>1</td>
       <td>0</td>
   </tr>
</table>

   <table border="1">
       <tr>
           <td colspan="2">~ (NOT)</td>
       </tr>
       <tr>
           <td>입력1</td>
           <td>입력2</td>
       </tr>
       <tr>
           <td>0</td>
           <td>1</td>
       </tr>
       <tr>
           <td>1</td>
           <td>0</td>
       </tr>
   </table>
   
---

#### 관계연산자
```
관계연산자는 2개 또는 그 이상의 값을 비교하여, 대소 관계를 나타내기 위한 연산자이다.   
주로 조건문에 많이 활용이 된다.
```
```java
public static void main(String[] args) {
    // == 연산자
    System.out.println(1 == 1); // true
    System.out.println(1 == 0); // false
    // != 연산자
    System.out.println(1 != 1); // false
    System.out.println(1 != 0); // true
    // > 연산자
    System.out.println(1 > 1); // false
    System.out.println(1 > 0); // true
    // >= 연산자
    System.out.println(1 >= 1); // true
    System.out.println(1 >= 0); // true
    // < 연산자
    System.out.println(1 < 1); // false
    System.out.println(1 < 0); // false
    // <= 연산자
    System.out.println(1 <= 1); // true
    System.out.println(1 <= 1); // false
}
```
---
#### 논리 연산자

대체적으로 비트연산자와 연산방법이 같으며, boolean 타입을 논리적으로 연산하는 방법이다.   
`논리곱인 &&(AND)` 연산할 경우 입력의 값이 `둘 다 1(true)면 true`가 반환된다.   
`논리합인 ||(OR)` 연산할 경우 입력의 값이 `둘 중 하나라도 1(true)이 있으면 true`가 반환된다.   
`단항 연산자 !(NOT)`는 1(true)일 때, 0(false)를 0(false)일 때, 1(true)를 반환한다.   
```java
public static void main(String[] args) {
  System.out.println(true && false); // false
  System.out.println(true || false); // true
  System.out.println(!true); // false
}
```
---
#### instanceof  
`instanceof`는 참조변수의 실제 타입을 알아보기 위해 사용한다.    
주로 조건문에 사용되며, `boolean값으로 반환`해주고 true가 나올경우 검사한 타입으로 `형변환`이 가능하다라는 것을 뜻한다.
```java
	public static void main(String[] args) {
		Parents p = new Parents();
		
		if (p instanceof Object) {
			System.out.println("true"); // true
		}
	}
```
만약에, `부모클래스가` 자식클래스를 `instanceof` 연산을 사용하여 형변환을 하려고한다면 어떤 값을 반환할까?
```java
	public static void main(String[] args) {
		Parents p = new Parents();
		
		if (p instanceof Children) {
			System.out.println("true");
		} else {
			System.out.println("false");
		}
	}
```
결론은 `false`를 반환하게된다. 부모가 자식이 되려했기 때문이다.
반대로, `자식클래스가` 부모클래스를 `instanceof` 연산을 사용하여 형변환을 하게될 경우이다.
```java
	public static void main(String[] args) {
		Parents p = new Parents();
		Children c = new Children();
		
		if (c instanceof Parents) {
			System.out.println("true");
		} else {
			System.out.println("false");
		}
	}
```
결론은 `true`를 반환하게된다.
이처럼, 부모는 자식이 될 수 없지만 자식은 부모로 `형변환`이 가능하다는 결론을 얻을 수 있었다.

---

