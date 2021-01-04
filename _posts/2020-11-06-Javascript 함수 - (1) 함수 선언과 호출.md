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
    - 객체 자료형 중 하나이기에 변수 대입 가능
    - 함수 생성시 함수명은 선택사항으로 함수명 없이 함수 생성 가능

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
- 일반적인 방법(기본 함수, 선언 함수)
- 함수 표현식으로 작성하는 방법(무명 함수, 익명 함수)

<br>

## 2 - 1. 일반적인 방법(기본 함수, 선언 함수)

- 선언 함수 : 이름을 가진 함수로 직접 호출이 가능
- 함수는 **스크립트 내 어디서나 선언** 가능
- **함수 호출**은 함수 선언 전후 상관없이 할 수 있지만, 가급적 **함수 선언 후 사용 권장**
- 기본 작성
    ```jsx
    function 함수명 (매개 변수1, 매개 변수2, ...) { //함수 선언
        실행 문장;
    }
    함수명(인자1, 인자2, ...); //함수 호출
    ```

- 간단한 함수 호출 예시

    1. 함수명 중복 선언 시, 마지막으로 선언된 함수가 호출됨
        ```jsx
        function num() {//num이라는 이름을 가진 함수
            alert("이름을 가진 선언 함수입니다.");
        }
        function num() {
            alert("나중에 선언된 함수가 호출됩니다.");
        }
        num();//함수 호출. 선언 함수의 경우 어느 곳에서나 호출 가능.
        ```
        ![https://blog.kakaocdn.net/dn/8vjc3/btqSdtEhIA7/1yPJduvT9c1iBpblvq2vhk/img.png](https://blog.kakaocdn.net/dn/8vjc3/btqSdtEhIA7/1yPJduvT9c1iBpblvq2vhk/img.png)
        같은 이름의 함수 재 선언 시 마지막에 선언된 함수가 호출됨.

    2. 함수 선언 전/후 호출 둘 다 가능
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

    3. 매개 변수와 인자 관계
        ```jsx
        function fx(fruits1, fruits2) {
                alert(fruits1);
                alert(fruits2);
            }
            fx("수박", "사과");//함수 fx의 fruits1에는 수박을, fruits2에는 사과를 전달
            fx("참외", "메론");

            fx("복숭아");//fruits1에만 인자 입력 시, 복숭아 알림 창 다음에 undefined(fruits2 인자 없음) 알림
        ```
        결과 : 수박, 사과, 참외, 메론, 복숭아, undefined 순으로 알림창

    4. ``<button>`` onclick 속성값으로 함수 호출하기 1

        ```html
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
        ```
        ![https://blog.kakaocdn.net/dn/o5hoG/btqSjAXaukK/Yytwc3VlAjABDaaJiAdku1/img.png](https://blog.kakaocdn.net/dn/o5hoG/btqSjAXaukK/Yytwc3VlAjABDaaJiAdku1/img.png)
    5. ``<button>`` onclick 속성값으로 함수 호출하기 2
        ```html
        <body>
            <!-- <button></button> 버튼의 역할이 전송일 때 쓰는 태그 ex. 로그인 페이지 -->
            <div class="btn" onclick="num()">함수 호출 버튼</div>
            <script>
                function num() {
                    let i = 1;
                    while(i<=10) {
                        document.writeln(i);
                        i++;
                    }
                }
            </script>
        </body>
        ```
        ![https://blog.kakaocdn.net/dn/Ptzlw/btqSpHBpD5f/TktjIcuPxFTkzROAuNfzE0/img.png](https://blog.kakaocdn.net/dn/Ptzlw/btqSpHBpD5f/TktjIcuPxFTkzROAuNfzE0/img.png)

    6. ``<button>`` onclick 속성값으로 함수 호출하기 3
        ```html
        <body>
            <div class="btn" onclick="fruits()">함수 호출</div>
            <script>
                //전역 변수: 문서 전역에서 사용.
                let num = 0;

                //선언함수: 어느곳에서든 호출 가능
                function fruits() {

                    //지역 변수: 함수 내에서만 실행되는 변수로 함수가 실행될 때마다 새로 만들어짐
                    // let a = 0;

                    num++;

                    if (num == 1) {
                        alert("사과");
                    } else if(num == 2) {
                        alert("수박");
                    } else {
                        alert("복숭아");
                    }
                }
            </script>
        </body>
        ```
        ![https://blog.kakaocdn.net/dn/EtaN2/btqSjBV7MnQ/potg1N5LWrod0eV8YSqh61/img.png](https://blog.kakaocdn.net/dn/EtaN2/btqSjBV7MnQ/potg1N5LWrod0eV8YSqh61/img.png)
        클릭마다 num++ 이므로, 사과(num==1), 수박(num==2), 복숭아(num==3), 복숭아(num==4), ..., 복숭아(num++), ...
    
    <br>
    
    ## 2 - 2. 함수 표현식으로 작성하는 방법(무명 함수, 익명 함수)

    - 함수 표현식을 선언하여 **변수에 할당**하는 방법
        - **변수를 함수명**으로 사용
        - **함수명이 생략**되기 때문에 **무명 함수** 혹은 **익명 함수**라고도 함
            1. 이름이 없기 때문에 변수에 대입하여 주로 사용.
            2. 함수 호출이 필요. 이름이 없기 때문에 반드시 함수를 호출하는 코드보다 먼저 작성되어야 함.
    - **함수 호출**은 함수 선언 전에는 불가능, **함수 선언 후 사용**
        - **함수 선언 전 호출하면 구문 에러(syntax error) 발생**
            ```jsx
            num();//익명 함수에서는 반드시 함수 다음에 호출해야 실행되기 떄문에 현재 이 호출은 실행되지 않음.

            let num = function() {
                alert("이름이 없는 익명함수입니다.");
            }
            num();
            num();
            num();
            num();
            ```
            ![https://blog.kakaocdn.net/dn/clWhtn/btqSDuno02F/dVjXR3y0vVduRNRXmaR8CK/img.png](https://blog.kakaocdn.net/dn/clWhtn/btqSDuno02F/dVjXR3y0vVduRNRXmaR8CK/img.png)
            실행되지 않음. 구문 에러 발생
    - 기본 작성
        ```jsx
        var 변수명 = function(매개 변수1, 매개 변수2, ...) {//함수 선언
            실행 문장;
        }
        변수명(인자1, 인자2, ...); //함수 호출
        ```
    - 간단한 무명 함수 호출 예시
        ```jsx
        var text1="함수 선언 전 호출 에러";
        var text2="함수 선언 후 호출만 가능";
        //printMsg(text1);  //함수 선언 전 호출 에러
        var printMsg=function(msg){//함수 객체 선언
            document.write("함수 호출 메시지 : " + msg + "<br>");
        }
        printMsg(text2);    //함수 선언 후 호출 가능
        ```

    <br>
    
    ---

    <br>

    - 기본 함수와 무명 함수가 **같은 이름**을 사용하면 **무명 함수가 호출**된다.
        ```jsx
        var printMsg=function(msg) {//무명 함수 선언
            document.write("무명 함수 : "+ msg + "<br>");
        }
        function printMsg(msg) {//기본 함수 선언
            document.write("기본 함수 : "+ msg + "<br>");
        }
        printMsg("호출되었습니다."); //함수 호출
        ```
        ![https://blog.kakaocdn.net/dn/cEw5ha/btqSjAbRWzs/C9K3140vG2TPPHv6ZsH8G0/img.png](https://blog.kakaocdn.net/dn/cEw5ha/btqSjAbRWzs/C9K3140vG2TPPHv6ZsH8G0/img.png)

