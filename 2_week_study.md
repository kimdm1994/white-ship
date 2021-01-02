### 2주차 과제 : 자바 데이터 타입, 변수 그리고 배열
---

목표                    
* 자바의 프리미티브 타입, 변수 그리고 배열을 사용하는 방법을 익힙니다
 
학습할것                 
* 프리미티브 타입 종류와 값의 범위 그리고 기본 값
* 타입과 레퍼런스타입
* 리터럴
* 변수 선언 및 초기화하는 방법
* 변수의 스코프와 라이프타임
* 타입 변환, 캐스팅 그리고 타입 프로모션
* 1차 및 2차 배열 선언하기
* 타입 추론, var     
---

<table border="1px">
        <th colspan="5">프리미티브타입 종류와 값의 범위 그리고 기본 값</th>
        <tr>
            <td>구분</td>
            <td>자료형</td>
            <td>크기(bit)</td>
            <td>값의 범위</td>
            <td>기본값</td>
        </tr>
        <tr>
            <td>논리형</td>
            <td>boolean</td>
            <td>8</td>
            <td>true, false</td>
            <td>false</td>
        </tr>
        <tr>
            <td rowspan="4">정수형</td>
            <td>byte</td>
            <td>16</td>
            <td>-128~127</td>
            <td>0</td>
        </tr>
        <tr>
            <td>short</td>
            <td>16</td>
            <td>-32,768 ~ 32,767</td>
            <td>0</td>
        </tr>
        <tr>
            <td>int</td>
            <td>16</td>
            <td>-2,147,483,648 ~ 2,147,483,647</td>
            <td>0</td>
        </tr>
        <tr>
            <td>long</td>
            <td>32</td>
            <td>-9,223,372,036,854,775,808 ~ 9,223,372,036,854,775,807</td>
            <td>0L</td>
        </tr>
        <tr>
            <td rowspan="2">실수형</td>
            <td>float</td>
            <td>64</td>
            <td>±1.4E-45 ~ 3.4E38</td>
            <td>0.0f</td>
        </tr>
        <tr>
            <td>double</td>
            <td>32</td>
            <td>±4.9E-324 ~ 1.8E308</td>
            <td>0.0</td>
        </tr>
        <tr>
            <td>문자형</td>
            <td>char</td>
            <td>64</td>
            <td>0~65,535</td>
            <td>'\u0000'</td>
        </tr>
    </table>   

```
기본(primitive) 데이터 타입이란 정수, 실수, 문자, 논리 리터럴을 직접 저장하는 타입을 말한다.
논리형(boolean), 정수형(byte, short, int, long), 실수형(float, double), 문자형(char)로 이루어져있다.
위의 표는 각 자료형에 대한 크기, 범위와 기본값을 보여준다.
각 타입별 저장되는 값의 범위는 기억할 필요가 없지만, 메모리 크기는 비트(bit), 바이트(byte)로 알아두면 좋을 것 같다.
메모리에는 0과 1을 저장하는 비트(bit)가 있고, 비트(bit) 8개를 묶어서 1바이트(byte)라고 표현한다.
변수마다 값의 범위를 어느정도 알아둘 필요가있다.   
```
<img src="https://github.com/kimdm1994/white-ship/blob/main/images/image.png" width="400px"></img>
```
변수마다 사용할 수 있는 값의 범위를 기억해야 하는 이유는, 변수마다 허용하는 값의 범위를 초과할 경우 
오버플로우(overflow)현상이 발생하기 때문이다.
```
출처 : <https://kingpodo.tistory.com/54>

```java
public class overflow {
   byte bNum = 127;
   byte result = (byte)(bNUm + 1);
   
   System.out.println("bNum의 크기 : " + bNum);
   System.out.println("result의 크기 : " + result);
}
```
```
bNum의 크기 : 127
result의 크기 : -128
```
---
### 프리미티브 타입과 레퍼런스 타입
```
자바의 데이터 타입으로는 프리미티브 타입과 레퍼런스타입이 있다. 
프리미티브 타입은 저장공간(변수)에 실제 리터럴 형태의 값이 저장된다.
레퍼런스 타입의 종류로는 클래스 타입, 인터페이스 타입, 배열 타입, 열거 타입으로 나누어져 있으며, 
실제 값이 아닌 해당 값을 참조하는 값이 메모리상에 저장된다.
```
```java
class Dog {
    String name;
    
    Dog(String t) {
        this.name = t;
    }
}

public class Exam_001 {
    public static void main(String[] args) {
        int age = 15;
        Dog d = new Dog(new String("a"));
        Dog d2 = new Dog(new String("b"));
        
        System.out.println(age);
        System.out.println(d.name + " " + d2.name);
    }
}
```
<img src="https://github.com/kimdm1994/white-ship/blob/main/images/image1.png" width="250px">

출처 : <https://blog.naver.com/chogahui05/221483768407>

```
위의 자료를 참조해서 직접 테스트를 해보았다.    
참고로 이클립스(eclipse)에서 디버그(Debug)에 대해서 잘 모르고있었는데, 이를 통해 배울 수 있는 계기가 되었다.    
결론을 말하자면, age라는 변수에는 리터럴 값이 15가 바로 출력이 되었다.   
하지만, new를 이용하여 객체를 생성한 후 "a"와 "b"를 출력하였을 때, 디버깅 결과 Dog이라는 결과값이 나오는걸 볼 수 있다.   
이러한 결과는 d와 d2가 Dog이라는 객체를 참조(reference)한다고 한다.    
결론적으로 프리미티브 타입과 레퍼런스의 차이는 실제 값을 저장하느냐, 
아니면 어딘가를 참조하기 위한 값을 저장하느냐의 차이라고 볼 수 있다.   
```
---
### 리터럴
```
리터럴(literal)이란 소스 코드의 고정된 값을 대표하는 용어이다.   
"고정된 값 = 변하지 않는"값 을 말하며, 하드코딩된 값 들을 말한다.   
아래 코드 7번줄에 10이라는 상수가 저장되었지만, 결과값에는 20이라는 상수가 저장된것을 볼 수 있다.   
리터럴은 소스코드에 고정된 값을 말하지만, 새로운 값을 변수에 대입하게되면 변경이 가능하다.   
```
```java
public static void main(String[] args) {
    int age:
    age = 10;
    age = 20;
    
    // 실수타입의 리터럴은 double타입으로 컴파일되기 때문에
    // float타입은 f or F를 명시해줘야한다.
    short s = 32767;
    int i = 100;
    long l = 10000L;
    float f = 0.123f;
    double d = 3.14;
    char c = 'A';
    String str = "ABC";
    
    System.out.println("int age : " + age);
    System.out.println("short s : " + s);
    System.out.println("int i : " + i);
    System.out.println("long l : " + l);
    System.out.println("float f : " + f);
    System.out.println("double d : " + d);
    System.out.println("char c : " + c);
    System.out.println("String str : " + str);
}
```
```
int age : 20   
short s : 32767   
int i : 100   
long l : 10000   
float f : 0.123   
double d : 3.14   
char c : A   
String str : ABC
```
---
### 변수 선언 및 초기화하는 방법
```
변수를 선언하고 처음으로 값을 저장하는 것을 변수 초기화 라고 한다.   
멤버 변수는 초기화를 하지 않아도 변수의 타입에 맞는 기본값으로 초기화가 이루어지지만   
지역변수는 사용하기 전에 반드시 초기화가 이루어져야한다.   
각 자료타입에 맞는 기본형은 위의 자료를 보면 알 수 있다.   
```
```java
public static void main(String[] args) {
    int a = 0; // 선언과 동시에 초기화
    int b; // 정수형 변수 선언
    b = 0; // 선언 후 초기화
}
```
---
### 변수의 스코프와 라이프타임
```
변수의 스코프(영역)이란 변수에 접근하거나 접근할 수 있는 유효 범위/영역이다.   
블록은 { 내용 }으로 이루어져있다.   
라이프타임은 변수가 메모리에서 살아있는 기간이다.   
변수의 스코프와 라이프타임이란 클래스 내부와 모든 메소드 및 블록 외부에서 선언된 변수이다.   
```
```java
public class Exam_001 {
    static int insValue = 10; // {}블록 내에 접근하기 위해 선언
    
    public static void main(String[] args) {
        insValue = 20; // 로컬 변수 20
        System.out.println("result : " + insValue);
    }
}
```
```
result : 20
```
출처 : <https://league-cat.tistory.com/411>
```
위의 결과처럼 {}블록 내에 접근하더라도 자신과 가장 가까운 값을 찾아서 저장하는 것을 알 수 있다.
```
---
`타입 변환, 캐스팅 그리고 타입 프로모션`
```
형변환 (boolean은 제외)   
 * 컴퓨터에서의 값 처리 규칙   
 1. 대입 연산자를 기준으로 왼쪽과 오른쪽은 같은 자료형이여야 된다.   
      다른 자료형의 값을 대입하고자 한다면 형변환이 필수이다.   
      자료형 변수명 = (자료형)값;   
 2. 같은 자료형끼리만 계산이 가능하다. --> 계산 결과도 같은 자료형으로 나온다.   

 1. 자동형 변환(묵시적형변환), 프로모션   
    - 자동으로 형변환이 이루어지기 때문에 우리가 형변환을 시켜줄 필요가 없다.   
    - 작은 데이터 타입에서 큰 데이터 타입으로 형 변환한다.   
 2. 강제형변환(명시적형변환)   
   - 범위가 큰 크기의 자료형을 작은 크기의 자료형으로 변환   
   - 형변환 연산자를 사용해야 한다.   
```
### 1. 프로모션 형변환
```java
public class D_Casting {
    public void casting() {
        short s = 12; 
        int i = s; // short -> int 자동형변환 됨
        long l = i; // int -> long 자동형변환 됨
        double d = i; // long -> double 자동형변환 됨
        double result = 12 + 3.3; // 12.0 + 3.3 = 15.3, int와 double 연산 시 int -> double로 형변환 후 연산
        long result2 = 30 + 30; // 30 + 30 = 60, 60을 long로 캐스팅하여 저장 -> 60L
        long result3 = 30 + 30L;
        
        float f = 1.0f;
        d = f;
        
        l = 10000000000L;
        f = l; // float가 long 보다 표현 가능한 수의 범위가 더 크기때문에 자동형변환이 가능
        
        int num = '문'; // 문자값의 유니코드 값을 대입한다.
        char ch = 65; // 숫자값이 들어오면 해당 숫자와 일치하는 문자를 유니코드 표에서 찾아서 대입한다.
        
        byte b1 = 1;
        byte b2 = 10;
        byte result4 = (byte)(b1 + b2); // byte나 short는 연산시 무조건 int형으로 처리해야한다.
        // (CPU 계산 처리단위가 4byte이기 때문!)
    }
}
```
```
s : 12
i : 12
l : 12
d : 12.0
result : 15.3
result : 60
result : 60
f : 1.0
d : 1.0
l : 10000000000
f : 1.0E10
num : 47928
ch : A
11
```
### 2. 명시적 형변환
```java
public void casting2() {
    double d = 4.0; // float f = d; -> #error
    float f =(float)d;
    int iNum = (int)d;
    
    iNum = 10;
    double dNum = 5.76;
    
    // 방법 1. 수행 결과를 int로 강제형변환
    int iSum = (int)(iNum + dNum); // 10.0 + 5.76 = 15.76 => 15
    // 방법 2. double 값을 int로 강제형변환 후 계산
    int iSum = iNum + (int)dNum;
    // 방법 3. double로 값을 받는다.
    double dSum = iNum + dNum; // 제일 쉬운 방법
    
    // byte, short 연산
    byte bNum = 1;
    short sNum = 2;
    
    byte bSum = (byte)(bNum + sNum); // bNum(int로 형변환) + sNum(int로 형변환)
    short sSum = (short)(bNum + sNum); // bNum(int로 형변환) + sNum(int로 형변환)
    int iSum2 = bNum + sNum;
    
    // 데이터 손실 테스트
    iNum = 290;
    bNum = (byte)iNum;
}
```
```
d : 4.0
f : 4.0
iNum : 10
bSum : 3
sSum : 3
iSum2 : 3

iNum : 290
iNum : 34
```
---
### 1차 및 2차 배열 선언하기
```
배열은 동일 타입의 값을 여러개 저장할 수 있다. [ ] 대괄호 안에 인덱스라 불리는 배열의 길이로 표기한다.
배열 표기법으로는
자료형[] 배열명;
자료형 배열명[];
배열명 = new 자료형[배열크기]; 이 있다.
```
```java
public void method1() {
    // 배열을 사용하는 이유
    int num1 = 1;
    int num2 = 2;
    int num3 = 3;
    int num4 = 4;
    int num5 = 5;
    
    // 합계
    int sum = num1 + num2 + num3 + num4 + num5; 
}
```
위 코드처럼 다량의 데이터저장을 배열을 이용하여 편리하게 저장하고자 한다.   
배열의 선언할 때에는 `자료형[] 변수명; // 메모리에(Stack) 정수형 배열의 주소를 보관할 공간을 할당 (참조변수)`   
배열을 할당할 때에는 `변수명 = new 자료형[index_value]` 형식으로 작성해준다.

배열을 따로 초기화 하지 않는다면, JVM이 지정한 기본 값으로 배열이 초기화 된다.   
배열을 선언하고 할당까지 해봤다면 출력하는 방법을 알아볼 것이다.   
배열을 출력하는 방법으로는 해당 인덱스를 출력하는 `System.out.println(배열명[배열크기]);` 방법이 있고,   
`for (int i = 0; i < 배열명.length; i++) {} ` 반복문을 이용한 방법이 있다.   
여기서 `.length` 는 배열의 길이만큼 출력하고싶다! 라는 뜻으로 쓰인다.

위의 3가지 방법외에 선언 후 바로 값을 넣어주는 방법도 있다.   
`int[] 배열명 = new int[] {val1, ..., ..., val(n)}` 값의 갯수만큼 자동으로 크기가 할당된다.

2차원 배열 표기법으로는 `자료형[][] 배열명;`, `자료형 배열명[행크기][열크기];`와 `자료형 배열명 = new 자료형[][];` 이 있다.
```java
public void method() {
    int[][] iArray1;
    int iArray2[][] = {{1, 2, 3, 4, 5}, {6, 7, 8, 9, 10}};
    int iArray3[];
    
    // heap 영역에 해당 크기만큼의 공간 할당
    iArray1 = new int[3][5];
}
```
이차원 배열을 출력할 때는 2중 for()문을 이용할 수 있다.    
```java
for (int i = 0; i < iArray1.length; i++) {
    for (int j = 0; j < iArray1[i].length; j++) {
        System.out.println(iArray1[i][j] + " ");
    }
}
```
바깥쪽 for()문은 `행의 개수`만큼 반복을하고, 안쪽 for()문은 `열의 개수`만큼 반복한다.    

---
### 타입추론, var
```
타입추론이란 개발자가 변수의 타입을 명시하지 않아도 컴파일러가 알아서 변수의 타입을 대입된 리터럴로 추론하는 것이다.   
var는 초기화값이 있는 지역변수(Local Variable)로만 선언이 가능하다.
var는 멤버변수, 메소드의 파라미터, 리턴 타입으로 사용이 불가능하다.
```
```java
public static void main(String[] args) {
    var str2 = "Hello type inference";
    
    if (str2 instanceof String) {
        System.out.println("str2 변수의 타입은 String 입니다.");
    }
}
```
`var`는 런타임 오버헤드가 없다.   
컴파일 시점에서 초기화 값을 보고 바이트코드에 명시적으로 `int는 int다`, `String은 String이다.`   
결정이 되있는 상태라 타입추론 변수를 읽을 때마다 타입을 알아내기 위한 연산을 하지 않는다.   
그래서 `var`로 선언된 변수는 중간에 타입이 절대 변경되지 않는다.

<img src="https://github.com/kimdm1994/white-ship/blob/main/images/image2.png" width="350px">   

이처럼 에러가 발생한다.
`var`는 초기화없이 사용할 수 없다. 초기화값을 선언부에 명시해줘야한다.
`var`타입 변수에는 `null`값이 들어갈 수 없다.
`var`타입은 로컬 변수에만 선언이 가능하다.
`Lambda Expression`에는 명시적인 타입을 지정해줘야 한다.   
배열을 선언할 때, `var`대신 타입을 명시해줘야 한다.

<img src="https://github.com/kimdm1994/white-ship/blob/main/images/image3.png" width="500px">   

출처 : <https://catch-me-java.tistory.com/19>

---

`#whiteship` `#2주차` `#live-study`
