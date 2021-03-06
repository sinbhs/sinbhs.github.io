---
layout: post
title:  "Javascript 기초"
date:   2020-09-02 19:31:29 +0900
categories: Javascript
---
# JAVA SCRIPT

## JavaScript 기초

### **Javascript 정의**

"웹 문서를 동적으로 제어하기 위해 고안된 프로그래밍 언어"


주기적으로 변하는 컨텐츠를 가진 기능이나 지도, 동적인 컨텐츠를 웹페이지에 적용할 수 있게 하는 스크립트 혹은 프로그래밍 언어이다.

<br>

---

<br>

### 자바스크립트 특징

1. 자바스크립트는 클래스, 상속의 개념이 없는 **객체 기반의 스크립트 언어**


2. **동적** **프로토타입(prototype)** 기반의 **객체 지향 언어** 


3. **객체 지향형 프로그래밍**과 **함수형 프로그래밍**을 모두 표현


4. 인터프리터/컴파일러형 언어 중 **인터프리터 언어**에 해당, 클라이언트의 웹 브라우저에 의해 해석되고 실행 (따라서 코드가 위에서 아래로 순차적 실행)


5. **HTML 문서 내에 기술**되는 스크립트 언어이며, **HTML 문서와 함께 수행**


6. CSS와 javascript 중 하나로 동적 컨텐츠를 구현할 수 있다면 **CSS 구현이 우선 (javascript가 호환되지 않는 브라우저가 있기 때문)**


7. CSS보다 **javascript가 우선 순위**

<br>

---

<br>

### 자바스크립트의 역할

- 요소의 추가 및 삭제 (HTML 페이지 변경 및 HTML 요소와 컨텐츠의 추가 및 삭제)
- CSS 및 HTML 요소의 스타일 변경
- 사용자와의 상호작용
- 폼의 유효성 검증
- 마우스와 키보드 이벤트에 대한 스크립트 실행
- 웹 브라우저 제어 및 쿠키 등의 설정과 조회
- AJAX기술을 이용한 웹 서버와의 통신
- 동적인 효과 이미지:hover 상태표시줄에 문자열 표시
- 웹사이트의 기능적인 면 쿠키처리, 새로운 윈도우 열기

---

### 자바스크립트 작성 유의사항

- **대소문자를 구분**하여 작성 
- HTML과 CSS는 기본적으로 대소문자 구별x, 하지만 자바스크립트는 대소문자를 구분하여 작성
    (a=10, A=10은 각각 다른 변수)
- **문장은 세미클론(;)으로 구분**
    한 행에 한 문장을 작성할 경우 세미클론(;)을 꼭 작성하지 않아도 된다.<br>
    >올바른 예시 )<br>
    `var age=25; //세미클론 생략 가능
    document.write("당신의 나이는 "+ age + "입니다.");//세미클론 생략 가능`

    >잘못된 예시 ) 한 행에 여러 문장 작성시 문장 마다 세미클론 필요<br>
    `var age=25 document.write("당신의 나이는 " + age + "입니다.")`
- **큰 따옴표("")와 작은 따옴표('') 구분**


    자바스크립트에서 큰따옴표("")를 사용했다면, HTML에서는 작은따옴표('')를 사용. 그 반대도 무관
    
    >ex ) `document.write("<div style='color:blue;'> 헬로 자바스크립트 </div>")`
- 자바스크립트는 **유니코드(unicode) 문자셋**을 사용
- **변수나 함수의 이름(식별자)을 작성**할 때는 **영문자, 숫자, 언더스코어(_), 달러($)만 사용** 가능. (but 첫글자로 숫자, 예약어 사용 불가)
    - 식별자 작성 방식 : Camel Case 방식/Underscore  Case 방식


        **Camel Case** : 식별자가 여러 단어로 이루어진 경우 첫 번째 단어는 모두 소문자로 작성하고, 그 다음 단어부터는 첫 문자만 대문자로 작성 (ex. userName)


        **Underscore Case** : 식별자를 이루는 단어들을 소문자로만 작성하며, 그 사이를 언더스코어(_)로 연결 (ex. user_name)
- 작성자나 다른 개발자가 나중에 코드를 수정할 때 참고할 수 있게 다는 설명문인 **주석(Comment)** 작성 방법
1. 한줄 주석 : //주석문
2. 여러 줄 주석 : /* 주석문 */ 


    >여러 줄 주석 내부에 한 줄 주석 삽입 가능<br>
    ```/* 여러줄 //이렇게 여러 줄 주석 안에 한 줄 주석 삽입 가능 주석입니다. */```
    여러 줄 주석 내부에 여러 줄 주석 중첩 사용 불가능<br>
    `/* 여러줄 주석 안에 /* 여러줄 주석 */ 을 넣을 경우 주석을 마치는 기호를 정상 인식하지 않음 */`

---

### 자바스크립트 포함 방법

1. 자바스크립트 코드 HTML 문서에 포함하는 방법

    ① HTML 문서 내부에 코드를 직접 작성하는 방법
    ② 자바스크립트 파일 별도 작성 후, HTML 문서에 참조하는 방법

1. 1 - 코드 작성 방법

    ```jsx
    <!DOCTYPE html>
    <html lang='ko'>
        <head>
            <meta charset='utf-8'>
            <meta http-equiv='X-UA-Compatible' content='IE=Edge'>
            <meta name='viewport' content='width=device-width, initial-scale=1, minimum-scale=1, maximum-scale=1, user-scalable=no'>
            <title>자바스크립트 기본</title>

            <!-- 자바스크립트 내부 작성 -->
            <script>
    						//자바스크립트 **내부 작성** 중 **<head> 태그 내 작성** 방법
            </script>

            <!-- 자바스크립트 **외부 문서 연결**. 스크립트 태그 사이엔 아무것도 작성하지 않음 -->
            <script src="script.js"></script>//같은 디렉토리에 있는 경우
        </head>

        <body>
    				<!-- 자바스크립트 내부 작성 -->
            <script>
                document.write('<h1>hello javascript!</h1>');//<body>태그 내 작성 방법
            </script>
        </body>
    </html>
    ```

    ① 자바스크립트 코드 `<script>`를 **`<head>`태그 또는 `<body>` 태그 내에 작성** - 간단한 코드, 보안상 나쁨

    `<script>` 코드는 `<head>`태그 내에 있는 것부터 실행된 후, `<body>` 태그 내에 있는 것이 실행됨.

    `<script>` 코드는 여러개 작성 가능

    ② 자바스크립트 파일 별도 작성 후, HTML 문서에 참조하는 방법 - 보안상 좋음

    ③ 위의 두 가지 방법을 혼합하여 사용 가능