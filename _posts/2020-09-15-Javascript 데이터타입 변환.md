---
layout: post
title:  "Javascript 데이터 타입 변환"
date:   2020-09-16 00:07:31 +0900
categories: Javascript
---
# 데이터 타입 변환

(데이터 타입 확인 방법은 전 게시글에 올린 typeof(변수명) 떠올리기 ^ㅇ^! )

<br>

- Javascript **데이터 타입을 변환하는 방법**은 두 가지 방법이 있다.
    - **암시적 변환**

        : 자바스크립트 엔진이 필요에 따라 자동으로 데이터타입 변환

    - **명시적 변환**

        : 개발자가 의도를 가지고 데이터 타입 변환 'Object(), Number(), String(), Boolean()'와 같은 객체 함수 사용

<br><br>

# I. 암시적 변환

- 암시적 변화란 연산 결과에 의해 데이터형이 자동으로 변화하는 것을 말한다.
- **+ 연산**을 할 경우, 숫자와 문자열, 불리언과 문자열로 더할 경우 모두 문자열로 변환한 후 문자열로 연결됩니다. (숫자보다 **문자열**이 우선시)

```jsx
// 더하기 (+)
console.log(10+11); //number + number = number(21)
console.log(10+"11"); //number + string = string(1011)
console.log("10"+"11"); //string + string = string (1011)

//문자열 + Boolean = 문자열
console.log("10"+true); //string + boolean = string (10true) 
```

- **다른 연산자(-, *, /, %)**는 더하기와 같은 문자형으로의 변환이 일어나지 않음 (문자열보다 **숫자**를 우선시)
    - true == 1, false == 0
    - null == 0
    - "" == 0
    - **산술 연산 특이 (자동변환)**
        - true는 1, false는 0
        - NaN은 NaN / undefined는 NaN
        - null은 0
        - ""(빈 문자열)은 0
        - console.log(true+true-false); [//true(1)+true(1)-false(0)](//true(1)+true(1)-false(0)) ⇒ 2
        - console.log(1+null); [//1+0](//1+0) ⇒ 1
    - **동치 비교(==)**
        - "0" == 0
        - 0 == false
        - "0"== false

<br>

---
<br>

# II. 명시적 변환

- 명시적 변환이란 **개발자가 의도적으로 데이터 타입을 변환**하는 것
- Object(), Number(), String(), Boolean() 등의 매서드 사용

<br><br>

## 1. 문자열을 숫자로 변환 Number()

: 숫자로만 되어 있는 문자열을 숫자로 변환

- **Number(변수명); Number 매서드 사용**

```jsx
<script>
const a = "234", b = "335", c="문자";
const sum1 = a + b ;
//Number(변수명); 숫자로만 되어 있는 문자열을 숫자로 변환
const sum2 = Number(a) + Number(b);

//결과 확인
console.log(sum1); //234335
console.log(sum2); //234+335 => 569

const total = Number(a) + Number(b) + Number(c);
console.log(total); // NaN(Not a number)
</script>
```

- **parseInt()**
    - 정수형의 숫자로 변환
- **parseFloat()**
    - 부동 소수점의 숫자로 변환
    - 10진수 사용

<br><br>

## 2. 숫자를 문자열로 변환 String()

: **다른 데이터형을 문자열로 변환**

- **String(변수명/값)**; 매서드 사용

```jsx
<script>
const a = "합계", b = 234, c = 654;
console.log(a+(b+c)); //합계888

//String(); 사용
console.log(a+(String(b)+String(c));//합계 234654
</script>
```

- **toString()**; 인자로 기수 선택 가능. 인자 전달 없을 시 10진수로 변환

```jsx
var a = 100;
a.toString(); //"100"
a.toString(2); //"1100100" (2진수)
a.toString(3); //"144"(3진수)
```

- **toFixed();** 인자값만큼 반올림하여 소수점 표현
    - 5~9 : 올림
    - 0~4 : 버림

```jsx
var b = 123.456789;
var c = 19.987654;

b.toFixed(); //"123"
b.toFixed(0); //"123"
b.toFixed(1); //"123.4"
b.toFixed(2); //"123.46"

c.toFixed(2); //"19.99"
c.toFixed(0); //"20"
```

<br><br>

## 3. Boolean 타입으로 변환

- **Boolean();** 매서드 사용

```jsx
Boolean(100); //true
Boolean(“1”); //true
Boolean(true); //true
Boolean(Object); //true
Boolean([]); //true
Boolean(0); //false
Boolean(NaN); //false
Boolean(null); //false
Boolean(undefined); //false
Boolean( ); //false
```