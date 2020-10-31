---
layout: post
title:  "Javascript 제어문 - (2) 반복문"
date:   2020-10-31 21:37:00 +0900
categories: Javascript
---
# 2. 반복문과 보조 제어문

- **반복문(loop statements)** : 동일 명령 여러 번 처리, 특정 연산 반복적 처리
    - **주어진 조건**에 따라 참과 거짓으로 구분. **true일 때 실행**.
    - for문, while문, do~while문

- **보조 제어문(break or continue statement)** : 조건문을 만나면 건너뛰거나 반복 수행 종료, 반복문 내에서 사용
    - continue문, break문

<br>
---

# 2 - 1. for문

- 반복 횟수에 중점을 둠. 조건이 만족되는 동안 반복 실행
    - 괄호 안에 두 개의 세미콜론(;)으로 분리된 세 개의 수식

        ```jsx
        for(초기식; 조건식; 증감식) {
        	실행 문장;
        }
        ```

        - 초기식 : 반복 변숫값 초기화. for문이 처음 시작할 때 단 한 번만 실행됨
        - 조건식 : 블록 내 문장을 얼마나 반복할지 결정. 조건식이 참(true)인 동안 반복
        - 증감식 : 초기식에서 초기화한 변수의 값을 증가 또는 감소시킴
    - 수식의 동작에 따라 블록 안의 문장 반복 실행
    - 조건식에 부합하면 반복문을 빠져나감

<br>

---

<br>

### · for문 작성 요령

<br>

ⓛ 초기식을 for문 이전에 먼저 선언했다면 for문에서는 생략 가능

```jsx
var num = 1; //초깃값 선언
for( ; num<=5; num++) {
    document.write("for문 수행 : <b>" + num + "</b> <p/>");
}
```

② 초기식 여러 개 선언 & 문자열st의 길이만큼 반복문 수행 방법

```jsx
var num;
var st="ABCDEF"; //문자열 길이 6
var ct;
for(num=1; ct=st.length; num<ct; num++) {//ct변수에 문자열 st의 길이 저장하는 초기식 추가
    document.write("for문 수행 : <b>" + num + "</b> <p/>");
    }
```

③ for문 블록 내에 증감식 문장을 포함한다면 for문 자체에서 증감식 생략 가능

```jsx
var num=1;
var st="ABCDEF";
var ct=st.length;
for( ; num<ct; ) {
    document.write("for문 수행 : <b>" + num + "</b> <p/>");
    num++;
}
```

④ for( ; ; )와 같이 초기식, 조건식, 증감식을 모두 작성하지 않으면 블록 내 문장 무한 반복, 이 경우에는 특정 조건을 만족하면 for문을 빠져나올 수 있도록 break문을 써주어야 함

```jsx
var num=1;
var st="ABCDEF";
var ct=st.length;
for( ; ; ) {
    if(num<ct) {
    	document.write("for문 수행 : <b>" + num + "</b> <p/>");
    	num++;
    	continue;
    }
    break;//if문(조건식)을 넣어 특정 조건을 만족하면 빠져나올 수 있도록 break문 작성
}
```

**①~④ 까지의 결과물은 다음과 같다.**

![1번~4번 예시 결과물](https://blog.kakaocdn.net/dn/bxGL90/btqMcREbSlk/3BcbBDNwdFvJUpOVXG40U0/img.png)

⑤ for문 안에 다른 for문 내포 가능 

- 간단한 예시 ( 구구단 프로그램 만들기)

    ```jsx
    var x, y;
    for(x=2; x<=5; x++){
        document.write("<b> --- [" + x + "단] --- </b>" + "<br>");
        for(y=1; y<=9; y++){
        	document.write(x + "*" + y + "=" + (x * y) + "<br>");
        }
    }
    ```

<br>

---

<br>

### for문을 이용한 다양한 예시들

1 ) 1부터 10까지의 합 구하기

```jsx
//1~10까지의 합 1+2+3+4+5+6+7+8+9+10 = ?
	let sum = 0;//값이 대입되어 있지 않거나 변수 선언이 되지 않은 채 작성되면 식 안에서 변수의 성격을 파악할 수 없기 때문에 숫자로 초기화.
	for(let i=1; i<=10 ; i++) {//변수 i를 1에 대입하고 1씩 증가되며 i가 10보다 작거나 같을 때까지 반복.
		sum += i;
	}
	document.body.innerHTML = "<h1>1부터 10까지의 합은 "+ sum +"입니다.</h1>";
```

![https://blog.kakaocdn.net/dn/dRRzUD/btqMcvg5Jxp/6TJRjLaWW629qeBKROrRzK/img.png](https://blog.kakaocdn.net/dn/dRRzUD/btqMcvg5Jxp/6TJRjLaWW629qeBKROrRzK/img.png)

2 ) 3, 5, 7, 9의 합 구하기

```jsx
//3+5+7+9의 합
let sum = 0;
for(let i = 3; i<=9; i+=2) {
	// sum = sum + i;
	sum += i;
}
document.body.innerHTML = "<h1>3+5+7+9의 합은 " + sum +"입니다.</h1>";
```

![https://blog.kakaocdn.net/dn/G9jcQ/btqMgthlpdS/iZUmZ5JrjGyDZ9yCYJrN1K/img.png](https://blog.kakaocdn.net/dn/G9jcQ/btqMgthlpdS/iZUmZ5JrjGyDZ9yCYJrN1K/img.png)

3 ) 구구단 2단 출력

```jsx
let sum = 0;
for (let i = 1; i<=9; ++i) {
	sum = 2 * i;
	document.writeln(2 + " * " + i + " = " + sum + "<br>");
}
```

![https://blog.kakaocdn.net/dn/KB5I5/btqMgt2JUKI/zqaNhk1Ycg7HZdVJP0c2t1/img.png](https://blog.kakaocdn.net/dn/KB5I5/btqMgt2JUKI/zqaNhk1Ycg7HZdVJP0c2t1/img.png)

4 ) 3의 배수이지만 7의 배수는 아닌(부정) 숫자만 출력

```jsx
for(let i = 1; i<=100; i++) {//1부터 100이 될 때까지(반복) -> 반복문
	if(i%3 == 0 && i%7 != 0) {//3의 배수이지만 7의 배수는 아닌(부정) 숫자만 출력 -> 조건문
    document.writeln(i);
    }
}
```

![https://blog.kakaocdn.net/dn/CSGw2/btqMegC5dhk/qKK8Ke89EEsC7XicKqyIwk/img.png](https://blog.kakaocdn.net/dn/CSGw2/btqMegC5dhk/qKK8Ke89EEsC7XicKqyIwk/img.png)

5 ) 구구단 2~9단 출력

```jsx
//구구단 2~9단 출력
let sum = 0;
for(let i = 2; i<=9; i++) {//2~9단
   document.write("<h2>-- " + i + "단 --</h2>");
   for(let j=1; j<=9; j++) {//각 단의 1~9까지의 곱하는 값
      sum = j * i;//구구단의 합
      document.write(i + " * " + j + " = " + sum + "<br>");
   }
}
```

6 ) 입력받은 구구단 출력

```jsx
let num = prompt("2단부터 9단 사이의 숫자를 입력하세요.");
let sum = 0;
if(num<=9 && num>=2) {
  document.write("<h1>--"+num+"단--</h1>");
  for ( let i = 1; i<=20; i++) {
      sum = i * num;
      document.write(num + " * " + i +" = "+ sum + "<br>");
  }
} else {
	  alert("2단부터 9단 사이의 숫자만 입력해주세요.");
  }
```

7 ) 별 트리 만들기

```jsx
for(let i = 1; i <= 8; i++) { //줄 수
	for(let star=1; star<=i; star++) {//별 수
	   document.write("*");
	}
   document.write("<br>");
}
```

![https://blog.kakaocdn.net/dn/b4FJ9f/btqMeFWUEXf/n0VlE4ATqPlzK8kqPCp6v1/img.png](https://blog.kakaocdn.net/dn/b4FJ9f/btqMeFWUEXf/n0VlE4ATqPlzK8kqPCp6v1/img.png)