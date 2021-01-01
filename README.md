### 1주차 자바 소스 파일(.java)을 JVM으로 실행하는 과정 이해하기
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

