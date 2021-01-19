:octocat: callback function
=================================================

#

## 콜백함수란?
    - 나중에 실행될 함수
    - 파라미터로 함수를 전달하는 함수 
    - 어떤 이벤트가 발생한 이후 수행될 함수 

>
```javascript
$("#myButton").on("click", function () {
     // 콜백 함수
      }); 
$.ajax({
    url : "URL", 
    type: "GET", 
    success: function () { 
         // 콜백 함수 
         }, 
    error: function () { 
        // 콜백 함수 
    }, 
    complete: function () {
        // 콜백 함수 
    }
});

```

#



## ※ 함수 객체 
    - 자바스크립트에선 함수를 객체로 취급
    - 따라서 다음 동작들이 가능
        - 1. 리터럴에 의한 생성
        - 2. 변수나 배열의 요소, 객체의 프로퍼티에 할당 가능
        - 3. 함수의 인자로 전달 가능
        - 4. 함수의 리턴값으로 리턴 가능
        - 5. 동적으로 프로퍼티 생성 및 할당 가능
    - https://velog.io/@mollang/js-함수-생성-함수-객체

#

## 콜백 함수가 필요한 이유 
    - 자바스크립트가 이벤트 기반 언어이기 때문
    - 비동기 처리
        - 특정 코드가 종료되지 않은 상태라 하더라도 대기하지 않고 다음 코드를 실행하는 자바스크립트의 특성(병렬적 실행)을 의미

    ``` javascript
            function first(){
        // Simulate a code delay
        setTimeout( function(){
            console.log(1);
        }, 500 );
        }
        function second(){
        console.log(2);
        }

        first();
        second();

        //2
        //1

    ```

## 어떻게 동작?
    - 함수를 콜백으로 다른 함수의 인자처럼 사용할 경우 오직 함수의 정의만을 넘겨주면 된다. 

    ```javascript
    setInterval(callback, 1000)
    ```

    ```javascript
    $("#btn_1").click(function() {
         alert("Btn 1 Clicked"); 
    });
    ```

## 원칙
    1. 이름이나 익명의 함수를 사용

    function(<매개변수1>, <매개변수2>,...)
    {
        코드...
    }

    - ※ 선언적 함수 
    function <function name>(<매개변수1>,<매개변수2>,...){
        코드...
    }
    2.콜백함수로 파라매터 전달

```javascript
//전역변수 
var generalLastName = "Clinton"; 
function getInput (options, callback) { 
    allUserData.push (options); // 전역변수를 콜백함수의 인자로 전달한다. 
    callback (generalLastName, options);
 }
```
    3. 콜백함수가 실행되기 전에 함수임을 명확하게 하기 
```javascript
//전역변수 
var generalLastName = "Clinton"; 
function getInput (options, callback) { 
    allUserData.push (options); 
    // 전역변수를 콜백함수의 인자로 전달한다. 
    callback (generalLastName, options);
     }

```
    4. this를 사용한 메서드를 콜백으로 사용시 문제
```javascript
var clientData = { 
    id: 094545, 
    fullName: "Not Set",
    // setUserName clientData의 메서드입니다. 
    setUserName: function (firstName, lastName) { 
        // this는 clientData라는 객체를 지칭하고 있습니다.
        this.fullName = firstName + " " + lastName;
         } 
    } 
    function getUserInput(firstName, lastName, callback ) {
         // Do other stuff to validate firstName/lastName here 
         // Now save the names 
         callback (firstName, lastName); 
    } 
    getUserInput ("Barack", "Obama", clientData.setUserName);
    console.log (clientData.fullName);
    // 값에 설정되지 않음 // fullName 프로퍼티가 window object의 인자로 세팅됨 
    console.log (window.fullName); // Barack Obama

```











## 콜백 함수 사용시 주의점
    - 콜백지옥(Callback Hall)
        - 비동기 처리 로직을 위해 콜백 함수를 연속해서 사용할 때 발생하는 문제
        - : 가독성이 떨어지고 로직 변경이 어려움

```javascript
$.get('url', function (response) {
	parseValue(response, function (id) {
		auth(id, function (result) {
			display(result, function (text) {
				console.log(text);
			});
		});
	});
});


```

    - 콜백지옥 해결방안
        - Promise나 Async를 사용
        - (코딩 패턴으로만 해결하고자 할 시) 각 콜백 함수 분리
        - https://velog.io/@yujo/JS%EC%BD%9C%EB%B0%B1-%EC%A7%80%EC%98%A5%EA%B3%BC-%EB%B9%84%EB%8F%99%EA%B8%B0-%EC%A0%9C%EC%96%B4


``` javascript
function parseValueDone(id) {
	auth(id, authDone);
}
function authDone(result) {
	display(result, displayDone);
}
function displayDone(text) {
	console.log(text);
}
$.get('url', function (response) {
	parseValue(response, parseValueDone);
});


```


