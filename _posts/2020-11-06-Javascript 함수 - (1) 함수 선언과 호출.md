---
layout: post
title:  "Javascript 함수 - (1) 함수 선언과 호출"
date:   2020-11-06 18:14:00 +0900
categories: Javascript
---
# 1. 함수 선언과 호출

- **함수** : 특정 기능을 수행하는 하나의 모듈로, 한번 선언해놓으면 여러 번 호출하여 사용 가능
    - 호출할 때마다 어떤 입력값을 주느냐에 따라 출력값이 다름
        > ex) 두 수의 곱셈을 구하는 함수 선언, 입력값으로 3, 5를 주면 15 출력 / 5, 4를 주면 20 출력

- **함수 선언 이유** : 한번 정의해놓은 작업을 필요할 때마다 호출하여 사용하기 위함
    - 함수 선언, 호출 형식은 다음과 같음
        ```jsx
        function 함수명(매개 변수1, 매개변수2, ...) {//함수 선언
            실행 문장;
            return 반환값;
        }
        함수명(인자1, 인자2, ...); //함수 호출
        ```
        - **함수명** : 함수 이름. 함수명 작성 규칙은 변수명 작성 규칙과 같음. 변수명으로 사용할 수 없는 것은 함수명으로 사용 불가능
        - **인자** : 함수를 호출할 때 전달하는 입력값
        - **매개 변수** : 함수 호출문에서 전달한 인자를 받기 위해 선언된 변수. 기본적으로 지역 변수로 정의되어 함수 내에서만 사용 가능
        - **function** : 함수를 선언할 때 사용하는 키워드
        - **return** : 함수에서 수행한 결괏값을 반환할 때 사용하는 키워드
    - 자바스크립트에서 **함수를 선언하고 호출하는 방법 2가지**
        - **일반적인 방법(기본 함수)**
        - **함수 표현식으로 작성하는 방법(무명 함수)**


<br>

---

# 2. 함수 선언 및 호출 방법
- 일반적인 방법(기본 함수)
- 함수 표현식으로 작성하는 방법(무명 함수)

<br>

## 2 - 1. 일반적인 방법

- 함수는 **스크립트 내 어디서나 선언** 가능
- **함수 호출**은 함수 선언 전후 상관없이 할 수 있지만, 가급적 **함수 선언 후 사용 권장**
    ```jsx
    function 함수명 (매개 변수1, 매개 변수2, ...) { //함수 선언
        실행 문장;
    }
    함수명(인자1, 인자2, ...); //함수 호출
    ```

- 간단한 함수 호출 예시
    ```jsx
    var text1 = "함수 선언 전 호출";
    var text2 = "함수 선언 후 호출";
    printMsg(text1); //함수 선언 전 호출
    function printMsg(msg) {
        document.write("함수 호출 메시지 : " + msg + "<br>");
    }
    printMsg(text2); //함수 선언 후 호출
    ```
    ![https://blog.kakaocdn.net/dn/GiGnf/btqMRk0he08/vaDhkhHys1Z8P1rRoPJAS0/img.png](https://blog.kakaocdn.net/dn/GiGnf/btqMRk0he08/vaDhkhHys1Z8P1rRoPJAS0/img.png)

- onclick 속성값으로 함수 호출하기
    - HTML5/JS

    ```
    <!DOCTYPE html>
    <html lang="ko">
    <head>
        <meta charset="utf-8">
        <meta http-equiv="X-UA-Compatible" content="IE=Edge">
        <meta name="viewport" content="width=device-width, initial-scale=1, minimum-scale=1, maximum-scale=1, user-scalable=no">
        <title>onclick 속성값을 이용한 함수 호출</title>
    </head>

    <body>
        <!-- button html  -->
        <button type="button" onclick="printMsg('홍길동',25)">학생 정보</button>

        <!-- button js -->
        <script>
            function printMsg(name, age){
            document.write("학생 이름 : <b>" + name + "</b><br>");
            document.write("학생 나이 : <b>" + age + "</b><br>");
            }
        </script>
    </body>
    </html>

    ```
    ![https://blog.kakaocdn.net/dn/brVOGR/btqM5TTBWrC/XGZm4f9LueVY7Fmv9zQ1k0/img.png](https://blog.kakaocdn.net/dn/brVOGR/btqM5TTBWrC/XGZm4f9LueVY7Fmv9zQ1k0/img.png) 클릭 시

    ![https://blog.kakaocdn.net/dn/P7R0u/btqNF84rtld/tTJRZDLIO8NdXkHUyqkim1/img.png](https://blog.kakaocdn.net/dn/P7R0u/btqNF84rtld/tTJRZDLIO8NdXkHUyqkim1/img.png)
    

    <br>
    

    ## 2 - 2. 함수 표현식으로 작성하는 방법(무명 함수)

    - 함수 표현식을 선언하여 변수에 할당하는 방법
        - 변수를 함수명으로 사용
        - 함수명이 생략되기 때문에 무명 함수라고도 함
    - **함수 호출**은 함수 선언 전에는 불가능, **함수 선언 후 사용**
        - 함수 선언 전 호출하면 구문 에러(syntax error) 발생
        ```jsx
        var 변수명 = function(매개 변수1, 매개 변수2, ...) {//함수 선언
            실행 문장;
        }
        변수명(인자1, 인자2, ...); //함수 호출
        ```