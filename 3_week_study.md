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
#### 대입 연산자
`대입 연산자`는 오른쪽의 값을 왼쪽의 값에 대입을 한다.
```
public static void main(String[] args) {
    int A = 3;
    int B = A; // B = 3
}
```
이처럼, `오른쪽에 있는 값`을 `왼쪽에 있는 변수`에 대입을 하게된다.   
대입 연산자의 종류는 `=, +=, -=, *=, /=, %=, &=, |=, ^=, <<=, >>=, >>>=`가 있는데,   
`A += B`를 예시로 설명하자면, `A = A + B`라고 할 수 있다.    
다른 연산자 기호도 같은 방법으로 연산하게 된다.   

---
#### 화살표 (-> 연산자)
람다식이란 함수를 따로 만들지않고 코드 한줄에 함수를 써서 호출하는 방식이다.
`JAVA 8` 부터 람다식(Lambda Expressions)을 지원한다.

람다식의 사용 방법으로는 `(매개변수, ...) -> {실행문 ... }`이며,   
매개 변수의 이름은 개발자가 자유롭게 지정가능하고 인자타입도 명시하지 않아도 된다.

`람다식 장점`
1. 코드를 간결하게 만들 수 있다.
2. 코드가 간결하고 식에 개발자의 의도가 명확히 드러나므로 가독성이 향상된다.
3. 함수를 만드는 과정없이 한번에 처리할 수 있기에 코딩하는 시간이 줄어든다.
4. 병렬프로그래밍이 용이하다.

`람다식 단점`
1. 람다를 사용하면서 만드는 무명함수는 재사용이 불가능하다.
2. 디버깅이 까다롭다.
3. 비슷한 함수를 중복생성할 가능성이 높다.
4. 재귀로 만들경우 다소 부적합한면이 있다.

참조 : <https://coding-factory.tistory.com/265>

---
#### 3항 연산자
3항 연산자는 if-else문과 같은 기능을 하며, 조건에따라 true 또는 false를 반환하는 조건식이다.
`조건식? 조건식1:조건식2`으로 표기하며, 조건식이 `true`라면 조건식1을 반환하고 `false`라면 조건식2를 반환한다. 
```java
public static void main(String[] args) {
    int A = 10;
    int B = 20;

    System.out.println(( A > B ) ? true : false );
}
```
결과는 `true` 이처럼 활용만 잘 할경우 if-else문보다 `코드 간결화`를 할 수 있다.

---
#### 연산자 우선순위
연산자의 우선순위로는 `산술 > 비교 > 논리 > 대입` 순서이며, `단항 > 이항 > 삼항` 순서이다.
연산의 진행방향으로는 `왼쪽에서 오른쪽` 이고, 대입의 진행방향으로는 `오른쪽에서 왼쪽` 으로 수행된다.

<table border="1">
<tr>
   <th>우선순위</th>
   <th>연산자</th>
   <th>설명</th>
</tr>
<tr>
   <th>1</th>
   <th>(), []</th>
   <th>괄호, 대괄호</th>
</tr>
<tr>
   <th>2</th>
   <th>!, ~, ++, --</th>
   <th>부정, 증감 연산자</th>
</tr>
<tr>
   <th>3</th>
   <th>*, /, %</th>
   <th>곱셈, 나눗셈 연산자</th>
</tr>
<tr>
   <th>4</th>
   <th>+, -</th>
   <th>덧셈, 뺄셈 연산자</th>
</tr>
<tr>
   <th>5</th>
   <th><<, >>, >>></th>
   <th>비트단위의 쉬프트 연산자</th>
</tr>
<tr>
   <th>6</th>
   <th><, <=, >, >=</th>
   <th rowspan="2">관계 연산자</th>
</tr>
<tr>
   <th>7</th>
   <th>==, !=</th>
</tr>
<tr>
   <th>8</th>
   <th>&</th>
   <th rowspan="3">비트단위의 논리연산자</th>
</tr>
<tr>
   <th>9</th>
   <th>^</th>
</tr>
<tr>
   <th>10</th>
   <th>|</th>
</tr>
<tr>
   <th>11</th>
   <th>&&</th>
   <th>논리곱 연산자</th>
</tr>
<tr>
   <th>12</th>
   <th>||</th>
   <th>논리합 연산자</th>
</tr>
<tr>
   <th>13</th>
   <th>?:</th>
   <th>조건 연산자</th>
</tr>
<tr>
   <th>14</th>
   <th>=, +=, -=, *=, /=, %=, <<=, >>=, &=, ^=, ~=</th>
   <th>대입, 할당 연산자</th>
</tr>
</table>

---
#### (optional) Java 13. switch operator
`기존 switch 구문`
```java
public void printDay(Day today) {
    switch (today) {
        case MON:
        case TUE:
        case WED:
        case THUR:
        case FRI:
	    System.out.println(today.name() + " is Weekday");
	    break;
        case SAT:
        case SUN:
            System.out.println(today.name() + " is Weekend");
	    break;
    }
}
```
`break`의 위치에 따라 실행 결과가 달라질 수 있기 때문에 개발자가 의도적으로 `break`를 했는지 실수인지 파악하기 어렵다.   

`강화된 switch 표현식`
```java
public void printDay(Day today) {
    switch (today) {
        case MON, TUE, WED, THUR, FRI -> System.out.println(today.name() + " is Weekday");
        case SAT, SUN -> System.out.println(today.name() + " is Weekend");
    }
}
```
여러 조건에 따라 `', '`로 구분해서 한 번에 처리할 수 있다.   
단일 실행으로 `->`만 추가했지만, `{ }` 형태로 구문을 만들 수 있다.   
`->` 대신 `:`를 사용해서 예전 방식으로 사용할 수 있다.   
`반환값이 있는 표현식을 블록('{ }') 구문으로 사용`
```java
public String printDay(Day today) {
    String result = switch (today) {
        case MON, TUE, WED, THUR, FRI -> today.name() + " is Weekday";
        case SAT, SUN -> {
            System.out.print("Holiday! ");
            yield today.name() + " is Weekend";
        }
    };
    return result;
}
```
`yield` 키워드를 사용해서 반환, `return` 키워드를 사용하면 컴파일 에러가 발생한다.   

출처 : <https://dev-kani.tistory.com/21>

---
`#live-study` `#white-ship`
