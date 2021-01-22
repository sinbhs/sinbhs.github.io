---
layout: post
title:  "크로스 브라우징(Cross Browsing)은 무엇일까?"
date:   2021-01-19 23:53:00 +0900
categories: Publishing
---

### **크로스 브라우징이란 정확하게 무엇일까?** 🤔

<br>

최근까지 **크로스 브라우징**이란 모든 브라우저에서 **동일한 정보**를 가진 웹 사이트를 제공하도록 웹 표준성을 지키고 호환성을 제공한다는 의미를 가지고 있는 줄 알고 있었다.


<br>

지금까지는 웹 표준 검사를 위한 [W3C validator](https://validator.w3.org/) 사이트와<br>호환성 체크를 위해 [Can I Use](https://caniuse.com/) 사이트를 사용하여 나름 크로스 브라우징을 신경쓰고 있다고 생각했는데 ...&#128172;
> 캔아이유즈 사이트를 이용하여 적용하고자 하는 효과나 동작(CSS, JS ...)이 각 브라우저에 지원되는지를 파악하고, 지원되지 않는다면 모든 브라우저에 지원되는 비슷한 효과를 찾아 적용하곤 했었다.

<br>

&#10060; 🙅‍♀️ &#10060;	

크로스 브라우징에 대한 정의가 잘못되었다는 것을 알았다.

제대로 된 정의를 알고 싶어

검색을 통해 공부해 보는 겸.

정리도 하면서 포스팅을 해보기로 했다.

<br>

### 크로스 브라우징 바로잡기

크로스 브라우징이란 **다양한 브라우저**(크롬, 사파리, 파이어폭스, 삼성 인터넷, 오페라, UC 브라우저, 엣지, IE, 기타 등등..)에서 사용자가 **동등한 수준의 정보와 기능에 접근**할 수 있도록 어느 한 쪽에만 최적화되어 치우치지 않게 **웹 접근성을 준수**하고 **호환성을 확보**하는 것이라고 한다.

<br>

=> 동일한 화면을 보여주는게 중점이 아니라

**사용자에게 동등한 정보와 기능을 제공**하는 것에 중점.

<br>


 ---

# 크로스 브라우징

## 크로스 브라우징이란?

<br>

- 웹 표준, 호환성을 지켜 사용자가 다양한 환경(기기, 브라우저)에서 동등한 수준의 정보, 기능에 접근 가능하도록 함
- 브라우저마다 렌더링 엔진(혹은 자바스크립트 엔진)이 달라서 발생
    - 렌더링 엔진 : HTML 문서 파싱, CSS 마크업 파싱 => DOM 트리 구축

    |브라우저|렌더링 엔진|설명|
    |------|---|---|
    |IE|<del>트라이던트(Trident)|(구)마이크로 소프트..뒤쳐진 엔진으로..점유율만 봐도 사실상 퇴역|
    |Edge|EdgeHTML, Blink|윈도우10 기본 브라우저인 마이크로소프트 엣지의 엔진. |
    |Chrome|Webkit, Blink|구글은 블링크 엔진(Webkit 코드 베이스에서 7천 개의 파일 삭제/최적화하여 개발),  iOS 한정 Webkit 엔진(iOS에서 Webkit만 사용 허가)|
    |Safari|Webkit2|애플 오픈 소스 개발 엔진. 현재는 웹킷 프로젝트로 분리되어 개발|
    |FireFox|개코(Gecko)|모질라 재단 후원. 오픈 소스 개발 엔진|
    |Opera|프레스토(Presto)|오페라 소프트웨어 개발 엔진. 가벼움, 낮은 점유율로 휴대 기기, 게임 콘솔 환경에선 메이저 엔진|
    |삼성 인터넷|블링크(Blink)|모질라 재단 후원. 오픈 소스 개발 엔진|

    출처 : [나무위키&#127795;](https://namu.wiki/w/%EC%97%94%EC%A7%84/%EC%9B%B9%20%EB%B8%8C%EB%9D%BC%EC%9A%B0%EC%A0%80)


<br>

## 크로스 브라우징 작업

<br>

1. 도움이 되는 사이트(웹 표준 검사, Can I use) 확인해보기

    - [웹 표준 검사](https://validator.w3.org/) : W3C Validator 
    - [Can I use](https://caniuse.com/) : 브라우저 기능 지원 체크 사이트(최대한 모든 브라우저에 지원되는 기능을 사용하자)

<br>

2. 초기화 작업하기(reset.css, normalize.css)

    - 브라우저마다 차이가 나는 기본 스타일 값 초기화

<br>

3. 그 밖의

    - 벤더프리픽스 : CSS 속성 접두어

        ex) -webkit-transform : translateX(-100%);
        |브라우저|접두어|
        |------|---|
        |IE|-ms-|
        |Chrome|-webkit-|
        |Safari|-webkit-|
        |FireFox|-moz-|
        |Opera|-o-|
    - 핵(Hack) 사용 : 추천X
    - 버전에 따라 IE용 주석(Conditional comments)
        ```
        <!-- [if IE 7]>
        <link href="ie7.css" type="text/css" rel="stylesheet"/>
        <![endif]-->

        <!-- [if IE 8]>
        <p> 이 문구는 IE8이 포함되지 않은 하위 브라우저, 즉 IE7,6에서 보여지게 됩니다.</p>
        <![endif]-->
        ```
    - 메타 태그 이용(IE) : 가장 최종 버전으로 맞춤
        ```
        <head>
        // ...
        <meta http-equiv="X-UA-Compatible" content="IE=edge"/>
        //...
        </head>
        ```
        
    출처: [Zzolab Project](https://okayoon.tistory.com/entry/크로스-브라우징cross-browsing)

<br>

4. 브라우저 점유율 보고 대응하기 (회사 기준에 따라)
    - [StatCounter](https://gs.statcounter.com/) 에서 전 세계/한국 브라우저 점유율 파악해보기
        - 2019.12 ~ 2020.12 전 세계 기준 :<br> Chrome(63.38%) > Safari(19.25%) > FireFox(3.77%) > Samsung Internet(3.47%) > Edge(3.08%) > Opera(2.26)%