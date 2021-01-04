---
layout: post
title:  "Javascript 함수 - (2) 반환값 출력"
date:   2021-01-04 16:07:00 +0900
categories: Javascript
---
# 반환값 출력

- **return의 역할**
    1. **데이터 반환. return 뒤에 오는 값을 함수의 결과로 반환**
    - 함수 수행 결과값(데이터)을 반환할 때 'return' 키워드 사용
    - 반환할 결괏값이 없다면 return문 생략 가능
    - return 뒤에 오는 값을 함수의 결과로 반환
    - 함수 안에서 선언된 변수나 값의 경우 외부에서의 접근이 불가능하기 때문에 매개변수(인자)와 리턴 키워드를 사용
    - 반환값을 저장하기 위한 변수는 미리 선언해 놓아야 함
        - [기본 작성]에 있는 result가 반환값을 저장하는 변수
    - 함수 처리가 완료되면 자동으로 함수를 호출한 시점으로 돌아가 프로그램 계속 수행
    - 기본 작성
        ```jsx
        function 함수명(매개 변수1, 매개 변수2, 매개 변수3) {//함수 선언, 매개변수 1, 2, 3을 이용하여 매개 변수 값 반환
            실행 문장;
            return 반환값;//함수 외부로 데이터 전달. 즉 함수 실행 후 결과를 다시 얻으려면 리턴 키워드 사용.
        }
        result=함수명(인자1, 인자2, 인자3); //함수 호출
        ```

    2. **함수 강제 종료. 함수 중간에 return하면 이후 모든 문장은 실행되지 않음.(break처럼)**
        ```html
        <head>
        <meta charset='utf-8'>
        <meta http-equiv='X-UA-Compatible' content='IE=Edge'>
        <meta name='viewport' content='width=device-width, initial-scale=1, minimum-scale=1, maximum-scale=1, user-scalable=no'>
        <title>return 3</title>
        <style>
            .btn {border:1px solid #000; width: 13%; padding:10px 6px; text-align: center; font-weight: bold; font-size:20px; cursor: pointer;}
            .btn:hover {background-color: #000; color:#fff;}
        </style>
        <script>
            //.onload = 하위 노드를 모두 불러왔을 때 이벤트 발생
            window.onload = function() {//문서 준비 이벤트
                // document.getElementById("btn").onclick = function() {}
                let btn = document.getElementById("btn");//문서 안의 아이디 값 호출
                btn.onclick = function() {//이벤트 연결
                    num();
                }
            }
        </script>
        </head>

        <body>
            <div class="btn" id="btn">함수 호출</div>
            <script>
                function num() {
                    alert("a");
                    return;//강제 종료
                    alert("b");
                }
            </script>
        </body>
        ```
        ![https://blog.kakaocdn.net/dn/dMv4BZ/btqSxCTUiaP/E6XIcqAJUUvadrnPMYZ6jk/img.png](https://blog.kakaocdn.net/dn/dMv4BZ/btqSxCTUiaP/E6XIcqAJUUvadrnPMYZ6jk/img.png)
        a 알림창 뜨고 종료됨. (b 알림창 뜨지 않음)


<br>

---

# 반환값 출력 예시

- 간단한 함수 호출 예시

    1. 변수 이용하여 반환값 호출
        ```jsx
        var result;
        function add(name, n) {
            document.write(name + " 학생이 1부터 " + n + "까지 덧셈 수행<br>");
            var sum = 0;
            for(var i=1; i<=n; i++) {
                sum+=i;
            }
            return sum;
        }
        result = add('홍길동', 10);
        document.write("결과 : " + result + "<p/>");
        result = add('이영희', 100);
        document.write("결과 : " + result + "<p/>");
        ```
        ![https://blog.kakaocdn.net/dn/bjN9DT/btqSjCgqOpo/SgP3CqSVjwFd9DNagxarj0/img.png](https://blog.kakaocdn.net/dn/bjN9DT/btqSjCgqOpo/SgP3CqSVjwFd9DNagxarj0/img.png)

    2. 변수 없이 반환값 출력
         - 출력문에서 바로 함수를 호출하면 됨
        ```jsx
        function add(name, n) {
            document.write(name + " 학생이 1부터 " + n + "까지 덧셈 수행<br>");
            var sum = 0;
            for(var i=1; i<=n; i++) {
                sum+=i;
            }
            return sum;
        }
        document.write("결과 : " + add('홍길동', 10) + "<p/>");
        document.write("결과 : " + add('이영희', 100) + "<p/>");
        ```
        ![https://blog.kakaocdn.net/dn/bjN9DT/btqSjCgqOpo/SgP3CqSVjwFd9DNagxarj0/img.png](https://blog.kakaocdn.net/dn/bjN9DT/btqSjCgqOpo/SgP3CqSVjwFd9DNagxarj0/img.png)

    3. 서로 다른 변수로 같은 함수의 반환값 출력
        - 자바스크립트에서는 함수는 변수에 할당하여 사용 가능
            - 함수 선언 후 함수명을 변수에 저장하는 방식
        - 여러 변수명으로 하나의 함수 사용 가능
        ```jsx
        function add(x, y) {
            return x+y;
        }
        var calSum = add; //함수를 변수에 할당
        var addUp = add; //함수를 변수에 할당
        document.write("결과 값 : " + calSum(5, 10) + "<br>");
        document.write("결과 값 : " + addUp(3, 20) + "<br>");
        ```
        ![https://blog.kakaocdn.net/dn/r38y2/btqSELbsmSE/WRNeT7Sw6xH4XQiXM1gs40/img.png](https://blog.kakaocdn.net/dn/r38y2/btqSELbsmSE/WRNeT7Sw6xH4XQiXM1gs40/img.png)