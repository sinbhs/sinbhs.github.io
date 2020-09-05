---
layout: post
title:  "Javascript 데이터 타입과 변수"
date:   2020-09-04 21:32:29 +0900
categories: Javascript
---
# 데이터 타입과 변수(variable)

# 데이터 타입

자바스크립트에서 사용하는 데이터 타입은 사용 용도에 따라 **기본형 타입(primitive type)**과 **객체 타입(object type)**으로 구분

- 데이터의 타입을 알아보기 위한 연산자 = typeof

    ex ) `console.log(typeof "홍길동");`  결과 값은 String

- 참과 거짓을 검증하는 함수 = Boolean()

    ex) `console.log(Boolean("hello"));` 결과 값은 true

[자바스크립트 데이터타입 - 기본형 타입](https://www.notion.so/aa4668b895b24f6ea206cf55dc234400)

<br><br>


---

# 변수(variable)

문자나 숫자 같은 데이터 값을 담는 데이터 저장 공간(메모리 공간) 으로 사용자가 이름을 붙여 사용

변수 값은 원할 때 언제든지 변경 가능

<br><br>



## 변수 키워드 var, let / 상수 키워드 const

<br>


### 변수 키워드 var, let

- **var**
    - **함수 레벨 스코프(Function Level Scope)**
    - 함수 내부 선언 변수 == 지역 변수 / 함수 외부 선언 변수, 키워드 생략 변수 == 전역 변수

        (지역함수는 함수 내에서만 유효)

    - **변수 중복 선언** **가능**

- **let**
    - **블록 스코프(Block Scope)**
    - 코드 블록(function, if문, for문 등) 내에서 선언된 변수는 블록 내에서만 유효 (지역 변수)
    - **변수 재할당 가능**하나, **같은 이름의 재선언 불가능**

<br>


### 상수 키워드 const

- **const**
    - **블록 스코프(Block Scope)**
    - 변하지 않는 값
    - 변수 **재선언, 재할당 모두 불가능**
    - 반드시 **선언과 동시에 값 대입**

<br><br>


## 변수 선언

- var 키워드와 함께 작성 var a(변수 명) = 10(값);
- 변수 여러 개를 한 문장으로 선언 시 쉼표 사용 `var a, b, c;`
- 변수 값 없이 변수 선언만 할 경우, 데이터 값은 undefined

    ```jsx
    var b;
    console.log(b); //변숫값이 없으므로 console창에 undefined값 나옴
    ```

- 함수(function) 내에 선언된 변수는 **지역 변수**로 함수 내에서만 유효.
**전역 변수**는 함수 외부에서 선언하여 코드 전 영역에서 사용가능한 변수
- var 키워드 생략 가능, 변수명 재선언해도 저장된 데이터  삭제x

<br><br>


## 변수명 규칙

- 변수명은 **특수문자를 제외**한 모든 **영문자로 시작** 가능
    - 다만 자바스크립트의 예약어 제외
- **문자, 밑줄(_), 달러 기호($)**로 시작하는 변수명 사용 가능
    - 숫자는 첫 글자로 사용 불가능
- **대소문자**를 구분
- 한글 사용 가능하지만 **영문자 사용** 권장
- 자바스크립트의 **예약어 사용 불가능**

    > 자바스크립트 예약어 : abstract, Arguments, boolean, break, byte, case, catch, char, class, const, continue, debugger, default, delete, do, double, else, enum, eval, export, extends, false, final, finally, float, for, function, goto, if, implements, import, in, instanceof, int, interface, let, long, native, new, null, package, private, protected, public, return, short, static, super, switch, synchronized, this, throw, throws, transient, true, try, typeof, var, void, volatile, while, with, yeild...

<br><br>


## 변수명 표기법

- **낙타 표기법(Camel case)**

    첫 단어는 *소문자*, 이후 추가 단어의 첫 글자를 *대문자*로 표기

    ex ) userName, userNumber, getLastName

- **파스칼 표기법(Pascal case)**

    첫 단어의 첫 글자도, 그 이후 추가 단어의 첫 글자도 *대문자*로 표기

    ex ) UserName, UserNumber, GetLastName

- **헝가리안 표기법(Hungarian case)**

    첫 번째 글자는 *데이터 타입*을 나타내는 소문자, 이후 추가 단어들은 파스칼 표기법에 따라 표기

    ex ) strUserName, numUserNumber, strGetLastName

<br><br>


## 변수값 대입

- 먼저 변수명 선언 후, **할당 연산자(assignment operator)인 "="를 사용** (같다의 의미가 아닌 우변을 좌변에 할당한다는 의미)
- 변수 선언 시 "="를 중심으로 좌변엔 변수명, 우변엔 변수, 연산식, 데이터 값 등이 옴

```jsx
var x; // 변수 x 선언
var y=10; // 변수 y 선언 및 초깃값 할당
var x=y; // 변수 y의 값을 변수 x에 저장
var a,b,c; // 변수 a,b,c 선언
var a=10, b=11, c=12; // 변수 a,b,c 선언 및 각각 다른 초깃값 할당
var a=b=c=10; // 변수 a,b,c 선언 및 같은 초깃값 할당
var name="홍길동", age=24 // 변수 name, age 선언 및 각각 다른 초깃값 할당
var total = a + b + c; // 변수 total 선언 및 변수 a, b, c의 값을 더한 결과를 변수 total 값으로 저장
```

<br><br>


## 지역 변수와 전역 변수

- 지역 변수 : 변수가 선언된 해당 블록에서 선언하여 범위 내에서만 유효하게 사용할 수 있는 변수
- 전역 변수 : 자바스크립트 코드 내 어느 위치에서든 선언하여 코드 전 영역에서 사용할 수 있는 변수

```jsx
<script>
	var globalValue1 = "홍길동" //전역 변수 선언 및 초깃값 할당
			globalValue2 = "아무개" //전역 변수 선언, var생략

			function 함수명(){
				var localValue; // 지역 변수 선언
						globalValue; //함수 내부에서 var 생략 시 자동 전역 변수로 선언
				localValue = 10; // 지역 변수 사용
			}

	globalValue=10; //전역 변수 사용
</script>
```

지역변수를 외부로 호출하기 위해서는 먼저 함수를 호출해야 사용 가능

함수 내 지역 변수 값을 출력하고 싶다면 함수 내부에 return 변수명; 을 작성해야 함.