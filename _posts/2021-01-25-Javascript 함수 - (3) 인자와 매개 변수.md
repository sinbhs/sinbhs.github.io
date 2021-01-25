---
layout: post
title:  "Javascript 함수 - (3) 인자와 매개 변수"
date:   2021-01-25 12:29:00 +0900
categories: Javascript
---
# 인자와 매개 변수


- 인자와 매개 변수는 **개수**도 같고, **데이터 타입**도 같음
    - **개수** = 프로그래밍 시 사용자가 작성
    - **매개 변수의 데이터 타입** = 인자의 데이터 타입에 따라 자동 결정(따로 설정 않아도 됨)

- 기본 작성
    ```jsx
        function 함수명(매개 변수1, 매개 변수2, 매개 변수3) {   //함수 선언
            실행 문장;
            return 반환값;
        }
        result = 함수명(인자1, 인자2, 인자3);   //함수 호출
    ```
    인자를 순서에 맞게 매개 변수에 대입하게 됨

- 이름이 같고 매개 변수의 개수가 다른 함수가 여러개 있으면 **맨 마지막에 선언된 함수가 호출됨**.

- 인자의 개수가 0이거나 매개 변수보다 적으면
    - NaN(Not a Number) 출력됨
        - NaN(Not a Number)은 연산 과정에서 잘못된 입력을 받았음을 나타내는 기호
        - 말 그대로 숫자로 반환하지 못할 때 출력됨
        - 자바스크립트에서 NaN은 전역 변수
        - NaN 여부는 isNaN() 함수를 사용하여 확인 가능
            ```jsx
            isNaN(NaN); //true
            isNaN('string'); //true
            isNaN(0); //false
            isNaN('0'); //false
            ```
- 인자의 개수가 매개 변수보다 많으면
    - 첫 인자부터 적용된 후 나머지 인자 값은 undefined 처리

---

<br>

# 인자의 개수에 따른 처리 결과 예시

<br>

1. 인자의 개수가 적거나 많을 경우 반환값 (+ 이름이 같고 매개 변수의 개수만 다른 함수가 여러번 선언 됐을 때)
    ```jsx
    function add() {
        var sum=1;
        return sum;
    }
    function add(x) {
        var sum=x+1;
        return sum;
    }
    function add(x,y) {
        var sum=x+y;
        return sum;
    }
    //위의 함수들은 마지막으로 선언된 함수로 인해 무시됨

    function add(x,y,z) {
        var sum=x+y+z;
        return sum;
    }   //이름이 같고 매개 변수의 개수만 다른 함수가 여러개 있으면 마지막에 선언된 함수만 호출됨
    var result0=add();
    var result1=add(1);
    var result2=add(2,3);
    var result3=add(4,5,6);
    var result4=add(7,8,9,10);
    document.write("함수 호출 인자 없음 : "+ result0 +"<p/>");
    document.write("함수 호출 인자 부족 : "+ result1 +"<p/>");
    document.write("함수 호출 인자 부족 : "+ result2 +"<p/>");
    document.write("함수 호출 인자 호출 : "+ result3 +"<p/>");
    document.write("7, 8, 9만 인자값으로 적용 : "+ result4 +"<p/>");
    ```
    ![예시1 결과](https://blog.kakaocdn.net/dn/Pdvtj/btqUtXbVeqK/7tR6DAVrJ1nZKjbXoe2ZwK/img.png)

    <br>

2. 인자의 개수가 적을 때 처리 가능하도록 하는 방법 예시
    - 정상적으로 처리될 수 있도록 프로그래밍 수정 예사
    - 제어문을 이용하여 처리되도록 수정
        ```jsx
        function add(x, y, z) {
            var sum;
            if((y===undefined) && (z===undefined)) {
                sum = x;
            } else if(z===undefined) {
                sum = x + y;
            } else {
                sum = x + y + z;
            }
            return sum;
        }
        var result1 = add(1);
        var result2 = add(1, 2);
        var result3 = add(1, 2, 3);
        document.write("함수 호출 인자 부족 :" + result1 + "<p/>");
        document.write("함수 호출 인자 부족 :" + result2 + "<p/>");
        document.write("함수 호출 인자 호출 :" + result3 + "<p/>");
        ```
        ![함수 인자 개수가 부족해도 결과가 나오게 하는 방법 예시2 결과](https://blog.kakaocdn.net/dn/8AvVQ/btqUJW3aKVi/Y3TpRlEIMCIwkyjkqMfEk1/img.png)
        
        이 방법은 인자의 개수가 너무 많거나 자주 변하는 경우, 적용하기 어려움(제어문 조건이 늘어남)

        아래의 방법으로도 해결 가능

        <br>

3. 인자의 개수에 맞게 작동하도록 프로그래밍하기

    - arguments 객체의 배열(array) 구조로 인자 처리
        - arguments[0], arguments[1], arguments[2] ... argument[n]과 같이 각 인자의 값을 배열에 저장하여 처리
        - arguments.length는 총 인자 수를 의미
        ```jsx
        function add() {
            var i, sum = 0;
            for(i=0; i<arguments.length; i++) {
                sum=sum+arguments[i];
            }
            document.write("수행 결과 : "+sum+"<p/>");
        }
        add(1, 2);
        add(1, 2, 3);
        add(1, 2, 3, 4);
        add(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);
        ```
        ![인자 개수에 맞게 작동하도록 프로그래밍하기 예시3 결과](https://blog.kakaocdn.net/dn/bvf0ma/btqUJYfDIZF/qnlDgz3kKPaXRUv2vX3ri0/img.png)