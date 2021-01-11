### 4주차 과제 : 제어문
---
목표
+ 제공하는 제어문을 학습하세요.

학습할 것
+ 선택문
+ 반복문

---
선택문
+ if 문
+ if - else 문
+ switch 문

### if 문
```java
if(조건식) {
    // 조건식이 true 일 때, 반환한다.
}
```
### if - else 문
```java
if(조건식) {
    // 조건식이 true일 때, 반환하고 else-if문으로 넘어가지 않는다
    // 조건식이 false일 때, else-if문을 수행한다.
} else if(조건식) {
    // 조건식이 true일 때, 반환한다.
    // 조건식이 false일 때, else문을 수행한다.
} else {
    // if, else-if문이 false일 때, 반환한다.
}
``` 
### switch 문
```java
switch(동등비교대상자) {
    case 값 1:
        // 실행코드1;
        break;
    case 값 2:
        // 실행코드2;
        break;
    case 값 3:
        // 실행코드3;
        break;
....
    default:
        //위 조건을 모두 만족하지 못할 경우 수행
}
```
`if 문` 과 다르게 실행코드를 실행하고 자동으로 빠져나가지 못한다. (`break`가 필요하다.)

---
반복문
+ for 문
+ while 문
+ do - while 문

### for 문
```java
for(초기식; 조건식; 증감식) {
    // 반복적으로 실행시키고자하는 실행구문
}
```
`초기식` 은 반복문이 수행될 때 `단 한번만 실행되는 구문` 이다.    
`조건식` 은 반복문이 수행될 `조건을 작성하는 구문` 이다.    
`증감식` 은 반복문을 제어하는 `변수 값을 증감 시키는 구문` 이다.     
초기식, 조건식, 증감식은 생략이 가능하다.(하지만 ` ; `은 반드시 필요하다.)
`for( ; ; )` 는 무한루프를 나타낸다.

```java
public void method2() {
  // 1부터 10까지 정수들의 합계
  // 1 + 2 + 3 + 4 + ... + 10
  int sum = 0;

  for (int i = 1; i <= 10; i++) {
    // sum = sum + i
    sum += i;
  }
  System.out.println("합계 : " + sum);
}
```
결과는 ` 합계 : 55 `를 출력한다.

### while 문
`while문` 은 조건식이 `true` 일 경우 해당 실행코드를 실행한다.    
조건식이 `false`일 경우 해당 반복문을 종료한다.     
횟수가 정해지지않은 반복 처리에 주로 사용된다.     
```java
while(조건식) {
    // 반복적으로 실행될 코드;
    // [증감식, 분기문]
}
```
`조건식` 이 true일 경우 해당 실행코드 실행      
`조건식` 이 false일 경우 해당 반복문을 종료한다.      
횟수가 정해지지않은 반복 처리에 주로 사용한다.     
```java
public static void main(String[] args) {
  int i = 0;
  int sum = 0;

  while (i <= 10) {
    sum += i;
    i++;
  }
  System.out.println("합계 : " + sum);
}
```
결과는 ` 합계 : 55 ` 를 출력한다.    

### do - while 문
```java
do{
    // 반복적으로 실행할 코드;
    // [증감식, 분기문]
} while(조건식);
```
`조건식` 이 true일 경우 해당 실행코드 실행    
`조건식` 이 false 일 경우 해당 반복문을 종료한다.    
횟수가 정해지지않은 반복 처리에 주로 사용된다.    
`while 문` 은 처음 수행될때도 조건식을 검사하고, `do - while 문` 은 첫 실행은 조건식에 관계없이 무조건 수행한다.

```java
public static void main(String[] args) {
  int sum = 0;
  int i = 0;

  do {
    sum += i;
    i++;
  } while (i <= 10);

  System.out.println("합계 : " + sum);
}
```
결과는 ` 합계 : 55 ` 를 출력한다.    
