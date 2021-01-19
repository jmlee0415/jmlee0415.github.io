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


