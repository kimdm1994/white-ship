### 1주차 과제 : 자바 소스 파일(.java)을 JVM으로 실행하는 과정 이해하기
---

목표                    
+ 자바 소스 파일(.java)을 JVM으로 실행하는 과정 이해하기.
 
학습할것                 
+ JVM이란 무엇인가
+ 컴파일 하는 방법
+ 실행하는 방법
+ 바이트코드란 무엇인가
+ JIT 컴파일러란 무엇이며 어떻게 동작하는지
+ JVM 구성 요소
+ JDK와 JRE의 차이
---
### JVM이란 무엇인가
Java Virtual Machine 의 `줄임말` 이며, `Java Byte Code` 를 OS에 맞게 해석해주는 역할을 한다.     
Java compiler 는 `.java` 파일을 `.class` 라는 `Java Byte Code` 로 변환 시켜 준다.        
Byte Code 는 기계어가 아니기 때문에 OS에서 바로 실행되지 않는다.        
이때, `JVM` 은 OS가 `Byte Code` 를 이해할 수 있도록 해석해준다.     
Byte Code 는 JVM 위에서 OS상관없이 실행된다. 이것이 Java의 가장 큰 장점이다.        
JVM 은 크게 `Class Loader`, `Runtime Data Areas`, `Excution Engine` 3가지로 구성되어 있다.         

**Class Loader**               
`RunTime` 시점에서 클래스를 로딩하게 해주며, 클래스의 인스턴스를 생성하면       
`클래스 로더` 를 통해 메모리에 로드하게 된다.       

**Runtime Data Areas**                   
`JVM` 이 프로그램을 수행하기 위해 OS로 부터 별도로 할당 받은 `메모리 공간` 을 말한다.

**Execution Engine**           
Load된 Class의 ByteCode를 실행하는 `Runtime Module` 이 `Execution Engine` 이다.       
실행 엔진은 자바 바이트 코드를 명령어 단위로 읽어서 실행한다.        

---
### 컴파일 하는 방법
자바 컴파일러는 자바를 가지고 작성한 자바 소스 코드를 `JVM` 이 이해할 수 있는 `Java Byte Code` 로 변환한다.
메모장이나 Notepad를 이용하여 테스트하고자 하는 소스코드를 작성해본다.(확장자명.java)
```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello World");
    }
}
```
코드를 작성하고 메모장에 옮겨서 확장자명을 .java로 변경해준다.       
`cmd` 를 열어주고, `cd~` 키워드를 통하여 `test.java` 파일이 있는 경로로 이동해주었다.       
경로가 이동한 뒤에 `dir` 키워드를 입력하여 현재 위치에 있는 파일들을 검색해본다.       
<img src="https://github.com/kimdm1994/white-ship/blob/main/images/image4.png" width="400px">       
`java`를 `.class파일`로 컴파일 하는 건 간단하다.          
해당 경로를 찾아가서 아래처럼 `javac` 명령어에 `java클래스명` 만 불러주면 된다.            
<img src="https://github.com/kimdm1994/white-ship/blob/main/images/image5.png" width="400px">    
출처 : <https://zorba91.tistory.com/247>        

---
### 실행하는 방법
컴파일을 정상적으로 완료하였다면, `java(패키지명/컴파일된 파일명)`을 입력하여 실행할 수 있다.            
<img src="https://github.com/kimdm1994/white-ship/blob/main/images/image6.png" width="300px">       

### 바이트코드란 무엇인가?
`자바 바이트 코드(Java Byte Code)란` 자바 가상 머신이 이해할 수 있는 언어로 변환된 `자바 소스 코드`를 의미합니다.          
자바 컴파일러에 의해 변환되는 코드의 명령어 크기가 1바이트라서 자바 바이트 코드라고 불리고 있습니다.            
이러한 `자바 바이트 코드`의 확장자는 `.class`입니다.            
자바 바이트 코드는 자바 가상 머신만 설치되어 있으면, 어떤 `운영체제`에서라도 실행될 수 있습니다.                   

---
### JIT 컴파일러 란 무엇이며 어떻게 동작하는지
인터프리터의 `단점을 보완`하기 위해 도입된 방식으로 바이트 코드 전체를 컴파일하여 `네이티브 코드로 변경`하고          
이후에는 해당 `메소드`를 더 이상 인터프리팅 하지 않고, `네이티브 코드`로 직접 실행하는 방식이다.               
하나씩 인터프리팅하여 실행하는것이 아니라 `바이트 코드 전체`가 컴파일된 네이티브 코드를 실행하는 것이기 때문에          
전체적인 실행 속도는 `인터프리팅 방식`보다 빠르다.         
<img src="https://github.com/kimdm1994/white-ship/blob/main/images/image7.png" width="400px">      

---
### JVM 구성 요소
+ 스택 기반 : x86 아키텍처나 ARM 아키텍처와 같은 `하드웨어`가 레지스터 기반으로 동작하는 데 비해 JVM은 `스택 기반`으로 동작한다.        
+ 심볼릭 레퍼런스 : 기본 자료형을 제외한 모든 타입(클래스와 인터페이스)을 명시적인 메모리 주소 기반의 레퍼런스가 아니라          
                   `심볼릭 레퍼런스`(참조하고자 하는 대상의 이름만으로 참조관계를 구성)를 통해 참조한다.          
+ 가비지 컬렉션(Garbage Collection) : 클래스 인스턴스는 사용자 코드에 의해 명시적으로 생성되고, 가비지 컬렉션에 의해 자동으로 파괴된다.     
+ 기본 자료형을 명확하게 정의 : C/C++등의 전통적인 언어는 플랫폼에 따라 int 형의 크기가 변한다.           
                              반면에 JVM은 명확하게 기본 자료형을 정의하여 `호환성`을 유지하고 `플랫폼 독립성`을 보장한다.
+ 네트워크 바이트 오더 : 역시 플랫폼 독립성을 유지하기 위하여 빅 엔디안, 리틀 엔디안과같은 바이트오더를               
                        네트워크 전송 시에 사용하는 네트워크 바이트 오더(빅 엔디안)를 사용한다.            
                        
JVM은 자바 실행코드가 `컴파일러`에 의해 자바 바이트코드로 변환된 것을       
각각의 하드웨어에 맞게 실행하는 개념으로 잡으면 나중의 이해에 도움이 될 것이라 생각한다.       

출처: https://odol87.tistory.com/5

<img src="https://github.com/kimdm1994/white-ship/blob/main/images/image8.png" width="400px">     
클래스 로더가 바이트 코드를 `런타임 데이터 영역`에 로드하고, 실행 엔진이 바이트코드를 실행하는 구조이다.

---
`#white-ship` `#live-study` `#1`
