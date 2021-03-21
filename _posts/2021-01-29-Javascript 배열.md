---
layout: post
title:  "Javascript 배열 - 배열 리터럴, 배열 객체"
date:   2021-01-29 13:46:00 +0900
categories: Javascript
---
# 배열(array)


- **여러 개의 '데이터'를 담는 특별한 변수**로 **인덱스 번호**로 관리. 배열은 **가변적**이다.

    - 여러 데이터를 모아 놓은 하나의 덩어리
        - 변수 == 하나의 데이터 값 저장 공간
        - 배열 == 여러 데이터 값 저장 공간

    - 배열에 저장된 하나의 데이터 == 원소

    - 각 원소는 0~n-1의 인덱스로 구분
        - [0, 1, 2, 4] <- 배열 작성 방식.
        - 인덱스 번호 0 1 2 3 (인덱스 번호는 0부터 시작)

<br>

- **배열 생성 방법**
    - **배열 리터럴(array literal)** : 배열 변수에 초깃값을 할당(대괄호 []를 사용)하여 배열을 만드는 방법 (배열은 0개 이상의 원소를 가짐)
    - **배열 객체(object)** : Array 생성자를 이용하여 배열 객체 생성

---

<br>

# 배열 생성 방법

<br>

## 1. 배열 리터럴(array literal)로 생성하기

**배열 리터럴 대괄호([ ])** 를 사용하여 만드는 방법

```jsx
// 배열 변수에 초깃값을 할당하여 배열 생성
var arr = [1234, 'one', true];

// 배열 변수 먼저 선언하고 원소 값은 따로 할당
var arr1 = [];
arr1[0] = "토끼";   //인덱스 0에 원소 할당
arr1[1] = 3;    //인덱스 1에 원소 할당
arr1[2] = "밀크티"; //인덱스 2에 원소 할당

console.log(arr1);  //Array(3). 0:"토끼". 1:3. 2:"밀크티". length: 3.

// 배열에 공백 데이터 넣기
var arr2 = [1, , 3, , 5]; //공백 리터럴 포함

console.log(arr2[1]); //undefined
```
- 배열명 : arr, arr1, arr2
- 배열 크기(length) : 원소 개수
- 배열 리터럴 : 대괄호([])
- 배열 원소 : 대괄호([]) 속 데이터 값들
- 각 원소들의 인덱스 : 0 ~ n-1

<br>

- 배열 내부에는 **다양한 데이터 타입**이 들어갈 수 있음
- 배열에 저장될 원소 개수를 모를 경우 var arr1=[];와 같이 선언.
    - 배열의 크기는 배열에 저장되는 개수만큼 자동 설정
- 배열은 명시되지 않은 원솟값을 undefined 처리
    - 공백 데이터가 있는 배열을 연산할 경우. 출력 결과가 제대로 나오지 않음
        - 제어문을 사용하여 공백 데이터 제외하여 처리하기
        ex. if(com[i] === undefined) {continue;}

<br>

```jsx
let arr1 = [1, 2, 3];//인덱스0:1, 인덱스1:2, 인덱스2:3.
let arr2 = [1, "string", true, function(){}, arr1, null, undefined];//숫자, 문자열, 논리, 함수, 변수, null, undefined ..

console.log(arr1);//Array(3). 0: 1. 1: 2. 2:3. length: 3.
console.log(arr2);//Array(7). 0: 1. 1: "string". 2: true. 3: f(). 4: (3)[1, 2, 3]. 5: null. 6: undefined. length: 7.
console.log(arr2[1]);//배열 요소 중 인덱스 번호 1 출력(string)
console.log(arr2[4]);//배열 요소 중 인덱스 번호 4 출력(arr1:[1,2,3])

arr1[0] = "문자열";//변수 arr1의 인덱스 번호0의 숫자를 "문자열"로 변경.
console.log(arr1); //Array(3). 0: "문자열". 1: 2. 2: 3. length: 3.
console.log(arr1[3]);//undefined
arr1[3]=4;
console.log(arr1); //Arrau(4). 0: "문자열". 1: 2. 2: 3. 3: 4. length: 4.
console.log(arr1.length);//.length 배열에 저장된 요소의 수.(변수명에 붙여 쓸 때) 4
console.log(arr2[1].length);//해당 인덱스 번호의 글자 수 출력.(요소 뒤에 붙여 쓸 때) 6(s,t,r,i,n,g)
```

<br>

## 2. 배열 객체(object)로 생성하기

**Array 생성자**를 이용하여 **배열 객체(object)** 만들기. new 연산자 사용

```jsx
var arr1 = new Array("Seoul", "Daegu", "Busan"); //초깃값 할당한 arr1 배열 생성
let arr2 = new Array();//빈 배열 선언.
let arr3 = new Array(5);//5개의 요소 없는 배열 선언. arr3 = [ , , , , ]
}
```