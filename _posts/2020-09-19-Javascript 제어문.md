---
layout: post
title:  "Javascript 제어문"
date:   2020-09-19 22:17:00 +0900
categories: Javascript
---
# 제어문

## 제어문이란?

- 프로그램 실행과정을 제어하기 위해 사용하는 구문
- **반복 처리 및 선택 처리**를 할 때 사용
    - **조건문(conditional statements)** : 조건에 따라 다음 문장 선택적 실행
        - if문, if~else문, 다중 if~else문, switch~case문
    - **반복문(loop statements)** : 동일 명령을 여러 번 처리하거나 특정 연산을 반복적으로 처리
        - for문, while문, do~while문
    - **보조 제어문(break or continue statement)** : 조건문을 만나면 건너뛰거나 반복 수행 종료, 반복문 내에서 사용
        - continue문, break문

---

# 1. 조건문

## 1 - 1. if문

- 조건식이 참(true)이면 블록 내의 문장을 처리, 거짓(false)이면 블록을 빠져 나감
- 조건식에 true 값을 직접 대입하면 무조건 처리하도록 제어 가능
- if문 안에 다른 if문 포함 가능

```jsx
if(조건식) {
	실행문장
	}

------------
if(조건식A) {
	실행문장;
	if(조건식B) {
		실행문장;
	}
}
```

## 1 - 2. if~else문

- 조건식이 참(true)인 경우와 거짓(false)인 경우 처리할 문장이 각각 따로 있을 때 사용
- 조건식이 2가지 결과값을 명확히 제어하고자 할 때 사용
-