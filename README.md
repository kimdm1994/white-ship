### 2주차 과제: 자바 데이터 타입, 변수 그리고 배열
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
```
**프리미티브 타입과 레퍼런스 타입**
자바의 데이터 타입으로는 프리미티브 타입과 레퍼런스타입이 있다. 
프리미티브 타입은 저장공간(변수)에 실제 리터럴 형태의 값이 저장된다.
레퍼런스 타입의 종류로는 클래스 타입, 인터페이스 타입, 배열 타입, 열거 타입으로 나누어져 있으며, 
실제 값이 아닌 해당 값을 참조하는 값이 메모리상에 저장된다.
```




    

