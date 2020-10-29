---
layout: post
title:  "Javascript 제어문 - 조건문"
date:   2020-09-20 18:48:00 +0900
categories: Javascript
---
# 1. 조건문

- **조건문(conditional statements)** : 조건에 따라 다음 문장 선택적 실행
- **주어진 조건**에 따라 참과 거짓으로 구분. **true일 때 실행**.
- if문, if~else문, 다중 if~else문, switch~case문

<br>
---

# 1 - 1. if문

- 조건식이 참(true)이면 블록 내의 문장을 처리, 거짓(false)이면 블록을 빠져 나감
    - 참 : 1, true
    - 거짓 : 0, null, "", undefined
    - if 조건문은 조건의 값이 참인 경우 실행되기 때문에 거짓(0, null, "",  undefined== false)의 조건에서는 실행되지 않음

    ```jsx
    //실행되지 않는 false의 값을 조건으로 가진 조건문
    let num1 = 0;
                if(num1) {//0 == false
                    alert(num1);
                }
                let num2 = null;
                if(num2) {//null == false
                    alert(num2);
                }
                let num3 = "";
                if(num3) {//"" == false
                    alert(num3);
                }
                let num4 =undefined;
                if(num4) {//undefined == false
                    alert(num4);
                }
    //거짓(0, null, "",  undefined== false)의 조건에서는 실행되지 않는다.
    ```

- 조건식에 true 값을 직접 대입하면 무조건 처리하도록 제어 가능
- if문 안에 다른 if문 포함 가능

    ```jsx
    if(조건식) {
    	조건이 참인 경우 실행문
    	}

    //if문 중복 사용 가능
    if(조건식A) {
    	실행문;
    	if(조건식B) {
    		실행문;
    	}
    }
    ```

- 간단한 예시

    ```jsx
    if(111<100) {alert('참입니다.')}; //조건이 거짓임으로 실행X
    if(0) {alert('참입니다')}; // 0 ==false, 실행x
    if(1) {alert('참입니다')}; // 1 == true, '참입니다.'알림 실행

    const num = 100;
    if(num>99) {alert(num+'은 99보다 큽니다.')}; //참이므로 실행
    if(num!=99) {alert(num+'와 99는 같지 않습니다.')}; //참이므로 실행
    ```

- 입력창(prompt)에 하루 걸음 수를 입력 받아 6000보 이상인 경우 '좋은 습관을 가지고 있습니다.' 출력하기

    ```jsx
    const walk = prompt('하루에 걷는 걸음 수를 입력하시오.');
    if(walk>=6000){ //참이면
    	alert('좋은 습관을 가지고 있습니다.');//출력
    }
    if(walk<6000) {
    	alert('운동이 필요합니다.')
    };
    ```

<br>

---

<br>

# 1 - 2. if~else문

- 조건식이 참(true)인 경우와 거짓(false)인 경우 처리할 문장이 각각 따로 있을 때 사용
- 조건식이 2가지 결과값을 명확히 제어하고자 할 때 사용
- if~else문 역시 다른 if~else문을 포함하여 작성 가능

    ```jsx
    if(조건식) {//조건이 참인 경우
    	실행문;//실행
    } else {//위의 조건이 거짓인 경우
    	실행문;//실행
    }
    ```

- 간단한 예시
    - 숫자를 받아 짝수인지 홀수인지 출력

    ```jsx
    const num = prompt('숫자를 입력하시오.');
    if(num % 2 == 0){ alert('짝수입니다.');} else { alert('홀수입니다.');}
    ```

    - 예/아니오 버튼 클릭 결과값에 따른 조건문

    ```jsx
    let member = confirm('회원 탈퇴를 하시겠습니까?');
    if(member) {//확인 버튼 클릭시 == true
    	alert('탈퇴 처리가 되었습니다.');
    } else {//취소 버튼 클릭시 == false
    	alert('탈퇴 취소 되었습니다.');
    }
    ```

    1 ) 나이가 19세 이상이면 성인, 미만이면 미성년자로 구분하는 프로그램

    ```jsx
    let age = prompt('당신의 나이를 입력해 주세요');
    if(age>=19) {//
    	result="성인입니다.";
    } else {
    	result="미성년자입니다.";
    }
    ```

    2 ) 주어진 변숫값을 판별하여 남자인지 여자인지, 성인인지 미성년자인지 구분하는 프로그램

    ```jsx
    var gender = "M"; //남자(M), 여자(F)
    var age = 21;
    if(gender == "M") {
    	if(age>=19) {
    		result="남자 성인입니다.";
    	} else {
    			result="남자 미성년자입니다.";
    		}
    } else {
    		if(age>=19) {
    			result="여자 성인입니다.";
    		} else {
    				result="여자 미성년자입니다.";
    			}
    }

    document.write("당신은 "+result);
    ```

    3 ) 로그인 프로그램 (ID=admin, PW=123456)

    1. HTML 문서

    ```html
    <!DOCTYPE html>
    <html>
    <head>
    	<meta charset = "utf-8">
    </head>
    <body>
    	<p>아이디, 비밀번호 입력</p>
    	<script src="스크립트 경로 혹은 주소"></script>
    </body>
    </html>
    ```

    2.   ID, PW 입력 자바스크립트

    ```jsx
    const id = "web", pw = "123456";
    //id: "web"
    //pw: "123456"
    const user_id = prompt('아이디를 입력하세요.');

    if (user_id == id) {
    	const user_pw = prompt('비밀번를호 입력하세요.');
    	if(user_pw === pw) {
    		location.href="login_page.html" //로그인 성공시 페이지 html 만들어서 연결
    	} else {
    			location.href="login_fail_page.html"//로그인 실패시 페이지 만들어서 연결
    		}
    else {
    	location.href="login_fail_page.html";
    }
    ```

    4 ) 입력한 걸음 수가 6000 이상이면 '좋은 습관을 가지고 있습니다.' 출력 / 입력한 값이 6000미만이면 '운동이 필요합니다.' 출력

    ```jsx
    const walk = prompt('하루에 걷는 걸음은 몇 보 입니까?');
    if (walk >= 6000) {
    	alert('좋은 습관을 가지고 있습니다.');
    } else {
    	alert('운동이 필요합니다.');
    }
    ```

<br>


---
<br>

# 1 - 3. 다중 if~else문 (else if)

- 여러 조건을 체크해야 할 때 사용
- 다중 if~else 문은 최악의 경우 마지막 else문에 도달할 때 까지 모든 조건식을 체크, 다중 선택이 많아지면 프로그램이 길어져 전체적인 흐름 파악 어려움 ⇒ switch ~ case 문은 이를 보완하는 다중 선택문

  ```jsx
  if(조건식a) {
    조건식a의 결과가 참일 때, 실행 문장;
  } else if(조건식b) {
    조건식b의 결과가 참일 때, 실행 문장;
  } else {
    위의 모든 조건을 만족시키지 못한 경우 실행
    조건식a, 조건식b 모두 거짓일 때, 실행 문장;
  }
  ```

- 0~100점 중 어떤 점수대에 포함되는지에 따라 학점을 A~F 5단계로 나누어 부여하는 학점 환산 프로그램

  ```jsx
  //90점 이상 A, 80점 이상 B, 70점 이상 C, 60점 이상 D, 그 이하는 F
  //입력한 점수와 함께 등급 출력
  let score = prompt('점수를 입력해 주세요.');
  score = Number(score);
  let grade; //등급 선언. 대입x

  if(score>=90 && score<=100) {
    grade = "A";
  } else if(score>=80 && score<=89) {
    grade = "B";
  } else if(score>=70 && score<=79) {
    grade = "C";
  } else if(score>=60 && score<=69) {
    grade = "D";
  } else {
    grade = "F";
  }

  document.body.innerHTML = '<h1>'+score+'점은 '+grade+'입니다.'+'</h1>';
  ```
<br>

<br>
---
<br>


# 1 - 4. switch ~ case 문

- 다중 if~else 문은 최악의 경우 마지막 else문에 도달할 때 까지 모든 조건식을 체크, 다중 선택이 많아지면 프로그램이 길어져 전체적인 흐름 파악 어려움 ⇒ switch ~ case문은 이를 보완하기 위해 사용하는 다중 선택문.
- 조건문을 체크하여 다음에 처리할 문장의 위치 파악 후 바로 해당 문장 처리
- 전체 조건식 체크할 필요가 없어 실행 속도가 다중 if~else문 보다 빠르다.
- switch(상수값) : 상수값으로 수치 또는 문자를 사용, 다음에 처리할 문장이 몇번째 case문에 해당하는지 표시
- case n ~ default: case 다음에는 수치나 문자, 그 다음에는 꼭 클론(;)<br>case에 해당하는 경우가 없으면 마지막 default문 수행<br> default 문에는 어떤 case문에도 해당하지 않는 경우에 처리할 문장 작성<br>default문을 작성할 필요가 없다면 사용하지 않아도 됨
- switch ~ case문 기본 형식

    ```jsx
    //switch 선택문 : 특정 값과 비교하여 참인 경우 실행
    switch(비교값) {
    	case 비교할 값1: 
    		실행문;
    		break;//비교값이 참인 경우 다음으로 넘어가지 않고 구문을 벗어남
    	case 비교할 값2:
    		실행문;
    		break;
    	default://위의 비교값과 일치하는 값이 없는 경우 실행. else와 같은 역할, 생략 가능
    }
    ```

- 간단한 예시

    ```jsx
    let num = prompt('1~4까지의 숫자 중 하나만 작성하세요.');
    num = Number(num);
    switch(num) {//비교 값에는 숫자, 문자열, 변수명 등등이 들어감
    	case 1:
    		alert('숫자 1입니다.');
    		break;
    	case 2:
    		alert('숫자 2입니다.');
    		break;
    	case 3:
    		alert('숫자 3입니다.');
    		break;
    	case 4:
    		alert('숫자 4입니다.');
    		break;
    	default:
    		alert('1~4 사이의 숫자만 입력해 주세요.');
    		break;
    }
    ```

    예시

    1) 원하는 사이트 입력시 해당 사이트로 이동

    ```jsx
    //window.location.href = ""; 사이트 이동
    //새창으로 띄울 땐 window.open('about:blank').location.href="주소"; 팝업창으로 띄우기
    let site=prompt("네이버, 구글, 다음 중 원하는 사이트를 입력하세요.");
    let url;

    switch (site) {
      case "네이버":
      //window.open('about:blank').location.href="https://www.naver.com";
    	  url = "naver.com";
    	  break;
      case "구글":
      //window.location.href="https://www.google.com";
        url = "google.com"
        break;
      case "다음":
        //window.location.href="https://www.daum.net";
        url = "daum.net"
        break;
      default:
        alert("제시된 사이트만 입력해 주세요.")
    }

    console.log(url);
    if(url) {//url 데이터가 있는 경우만 실행
    window.oepn("about:blank").location.href = "https://www." + url;
    }
    ```

    2) 1~4번 사이의 번호 입력시, 해당 번호의 이미지 출력 / 다른 번호 선택시, "1~4번 사이의 번호만 입력해주세요." 출력

    ```jsx
    const num =prompt("1~4번 사이의 번호를 입력해주세요.");
      switch (num) {
         case "1":
           document.body.innerHTML= "<img src='images/01.jpg' alt='dog'>";
           break;
         case "2":
           document.body.innerHTML= "<img src='images/02.jpg' alt='cat'>";
           break;
         case "3":
           document.body.innerHTML= "<img src='images/03.jpg' alt='whitedog'>";
           break;
         case "4":
           document.body.innerHTML= "<img src='images/04.jpg' alt='jjang9'>";
           break;
         default :
           alert("1~4번 사이의 숫자만 선택해 주세요.");
           window.location.reload();//새로고침
    }
    ```

    3) 입력받은 숫자가 짝수인지 홀수인지 알림

    ```jsx
    let num = prompt("숫자를 입력해 주세요.");
    //입력 받은 값이 홀수인 경우 "입력한 값 ..은/는 홀수 입니다." 출력
    //입력 받은 값이 짝수인 경우 "입력한 값 ..은/는 짝수 입니다." 출력
    //숫자 외의 값 입력시 "숫자만 입력해 주세요" 출력

      switch(num % 2) {//문자열이지만 식을 통해 자동으로 숫자로 변환되어 연산 -> 숫자형 데이터
         case 0://입력 받은 값이 짝수인 경우
           alert("입력한 값 "+num+"은/는 짝수입니다.");
           break;
         case 1://입력 받은 값이 홀수인 경우
           alert("입력한 값 "+num+"은/는 홀수입니다.");
           break;
         default:
           alert("숫자만 입력해 주세요.");
    }
    ```

    4) 4가지 음료 중 입력받은 음료의 가격 출력

    ```jsx
    //아메리카노:10000, 카페라떼:16000, 카페모카:17000, 바닐라라떼:20000
    //입력 받은 커피명을 통해 가격을 출력
    //"주문한 ..은/는 ..원입니다." 출력
    let coffee = prompt("아메리카노, 카페라떼, 카페모카, 바닐라라떼 중  선택해 주세요.");
    let price = "";
    /*
    변수 초기화
    1. 숫자 변수 초기화  let num = 0;
    2. 문자열 변수 초기화 let txt = "";
    3. 논리 변수 초기화 let bool = false;
    4. 객체 변수 초기화 let obj = null;
    */
    switch (coffee) {
       case "아메리카노":
          // alert("주문한 "+coffee+"는 10,000원입니다.");
          // document.write("주문한 아메리카노는 10,000원입니다.");
          price = "10,000";
          break;
       case "카페라떼":
          // alert("주문한 "+coffee+"는 16,000원입니다.");
          price = "16,000";
          break;
       case "카페모카":
          // alert("주문한 "+coffee+"는 17,000원입니다.");
          price = "17,000";
          break;
       case "바닐라라떼":
          // alert("주문한 "+coffee+"는 20,000원입니다.");
          price = "20,000";
          break;
       default:
          alert("제시된 커피명만 입력해주세요.");
    }
    if(price) {
    document.body.innerHTML = "<h1>주문한 " + coffee + "는" + price+"원입니다.</h1>";
    }
    ```

    5) 중첩 switch~case문 사용하여, 아이디를 입력 받아 참인 경우 비밀번호를 입력받고 비밀번호도 참인 경우 '로그인되었습니다.' 출력

    ```jsx
    let id = 'jw';
    let pw = 1234;

    let user_id = prompt('아이디를 입력해주세요.');
    switch(user_id == id) {//true
    	case true:
    		alert('아이디가 일치합니다.');
    		let user_pw = prompt('비밀번호를 입력해주세요.');
    		//입력받은 문자열
    		user_pw = Number(user_pw);//숫자형의 문자를 숫자로 변환
    			switch(user_pw) {
    				case 1234://케이스 값은 숫자
    					alert('로그인되었습니다.');
    					break;
    				default:
    					alert('비밀번호가 틀렸습니다.');
    			}
    			break;//비교값이 실행되면 다음을 읽지 않고 구문을 빠져 나옴
    	default:
    		alert('아이디가 불일치합니다.');
    }
    ```