---
layout: post
title: "[자바스크립트 스터디] 03.언어의 기초"
tags: [javascript, study]
comments: true
---

[자바스크립트 스터디] 03.언어의 기초

- 문법 훑어보기
  - ECMA-262에 ECMAScript라는 이름의 가상 언어로 정의했다.
  - ECMAScript의 문법은 C 언어, 자바나 펄 등 C와 비슷한 언어에서 차용한 것이다.

\[Think | 다양한 개발 언어를 공부한다는 가능성을 염두에 두고, 설명해주고 있다.]

- 대소문자 구분
  - 변수, 함수 이름, 연산자 모두 대소문자를 구분한다.
  - 'test와 Test', 'typeof와 typeOf'는 다르다.
- 식별자
  - 변수, 함수, 프로퍼티, 함수 매개변수의 이름이다.
  - 첫 번째 문자는 글자, 밑줄, 달러 기호 중 하나여야 한다.
  - 카멜 케이스로 쓴다. (ECMAScript의 내장 함수와 객체가 카멜 케이스로 표기되어 있어서 이 형식을 따르길 권한다.)

\[Think | 다른 책에서는 '첫 번째 문자는 숫자로 시작하면 안된다.' 정도로 알려줬었는데 이 책에서는 다양한 경우가 있다는 것을 알려주고 싶어 한다.]

- 주석
  - C 언어 스타일로 표기한다.
  - 한 줄 주석
    ```
      // 한 줄 주석
    ```    
  - 블록 주석<br>
    ```
      /*
        * 블록 // 가독성을 위해 추가한 것이다.
        * 주석 // 기업 애플리케이션에서는 이런 형태를 선호한다.
      */
    ```
- 스트릭트 모드
  - ECMAScript 5에서 도입했다.
  - 책의 내용이 너무 어려워서 이해가 안 됐다. (다른 블로그 글을 보니 '엄격하게 무시하겠다.'라고 생각하면 된다고 한다.)
  - 전체 스크립트에 스트릭트 모드를 적용하려면 다음 문장을 스크립트 맨 위에 추가한다.
    ```
      "use strict";
    ```
  - 함수 단 하나만 스트릭트 모드를 적용하려면 다음 선언을 함수 본문 맨 앞에 추가한다.
    ```
      function doSomething(){
        "use strict";  
      }
    ```
- 문장
    - ECMAScript에서 각 문장은 <mark>세미콜론</mark>으로 종료한다.
    - C 언어 스타일 문법을 써서 여러 문장을 <mark>코드 블록</mark>으로 합칠 수 있다.
      ```
        if (test){
          test = false;
          alert(test);
        }
      ```
- 키워드와 예약어
    - 키워드와 예약어는 식별자나 프로퍼티 이름에 쓸 수 없다.
    - 키워드는 제어문의 시작과 끝을 나타낸다거나 특정한 조작 목적으로 쓰인다.
    - 식별자 이름에 키워드 쓰려 하면 에러를 낸다. 예약어를 쓰려 하면 에러를 낼 수도 있고 에러가 없을 수도 있다.
    - ECMAScript의 키워드 전체
    break, case, catch, continue, debugger*, default, delete, do, else, finally, for, function, if, in, instanceof, new, return, switch, this, throw, try, typeof, var, void, while, with
    - ECMAScript 3판의 예약어 전체
    abstract, boolean,byte, char, class, const, debugger, double, enum, export, extends,final, float, goto, implements, import, int, interface, long, native, package, privat,e protected, public, short, static, super, synchronized, throws, transient, volatile
    - ECMAScript 5판의 예약어(일반 모드)
    class, enu, extends, super, const, export, import
    - ECMAScript 5판의 예약어(스트릭트 모드)
    implements, interface, let, package, private, protected, public, static, yield
- 변수
    - 변수를 정의할 때는 var 연산자 다음에 변수 이름을 씁니다.(키워드+식별자)
    - 변수의 데이터 타입을 바꾸는 행위는 유효하지만 권장하지 않는다.
    - var 연산자는 변수를 로컬 스코프에서 정의한다.
      - 책에 있는 예제
        ```
          function test(){
            var message = "hi"; // 지역 변수
          }
          test();
          alert(message); // 에러

          function test(){
            message = "hi"; // 전역 변수
          }
          test();
          alert(message);
        ```
      - 학원에서 배운 예제
        ```
          var test = function(){
            var message = "hi"; // 지역 변수
          };
          test();
          alert(message);

          var test = function(){
            var message = "hi"; // 전역 변수
          };
          test();
          alert(message);
        ```


    - 변수를 여러 개 선언하려면 쉼표로 구분한다.        
      ```
        var message = "hi",
            found = false,
            age = 29;
      ```

\[Think | 학원에서 배운 예제를 사용하면 지역, 전역 변수를 구분하지 않아도 전부 에러가 나지 않는다. 이렇게 사용했을 때의 문제점이 있을까요?]

- 데이터 타입
  - 원시(기본적인) 데이터 타입(Undefined, Null, boolean, Number, String) + 객체(Object)
  - typeof 연산자를 통해서 데이터 타입을 알 수 있다.
    ```
      var message = "some string";
      alert(typeof message); // string
      alert(typeof (message)) // string, 연산자이므로 괄호는 쓰지 않는다.
      alert(typeof 95); // number
    ```
  - undefined
    - 특별한 값
    - var를 써서 변수를 정의했지만 초기화하지 않았다면 undefined
      ```
        var message; // 초기화를 하지 않았다.
        alert(message == undefined); // true
      ```
    - typeof를 호출하면 선언되지 않은 변수와, 선언된 변수 두 다 undefined로 나온다.

  - null
    - 빈 객체를 가리키는 포인터
    - typeof를 호출하면 object로 반환한다.
    - 변수가 객체를 가리키게 할 생각이라면 null로 초기화한다.

  - boolean
    - true, false 두 가지의 리터럴 값만 가진다.

  - number
    - 스트릭트 모드에서는 8진법을 허용하지 않는다.
    - 부동소수점 숫자를 저장할 때는 메모리를 두 배로 소모하므로 가능 한 정수로 변환하여 저장해야 한다.
    - e-표기법(지수 표기법): e 앞의 숫자에 10을 e 뒤에 숫자만큼 곱한다.
      ```
        var floatNum = 3.125e7; // 31,250,000
      ```
    - NaN: Not a Number
      - 숫자를 반환할 것으로 의도한 조작이 실패했을 때 반환하는 값
      - isNaN(): 매개 변수를 하나 받으며 해당 값이 '숫자가 아닌 값'인지 검사한다. 숫자로 변환할 수 없는 값을 넘기면 true로 반환한다. 숫자로 바꿀 수 있거나 숫자이면 false이다.
    - 숫자 변환
      - Number()
        - 매개변수로 boolean 값을 넘겼다면 1, 0으로 바꿔서 반환
        - 매개변수로 숫자를 넘겼다면 그대로 반환
        - 매개변수로 undefined을 넘겼다면 0을 반환
        - 매개변수로 문자열을 넘겼다면 리딩 제로를 무시한다.
        - 빈 문자열은 0을 반환
      - parseInt()
        - 정수 형태의 문자열을 숫자로 바꿀 때 쓴다.


\[Think | undeifined는 정의는 됐지만, 초기화가 안 된 값을 의미하는 것일까요?]


- 연산자
- 문장
- 함수
  ```
    function sayHi(name, message){
      alert("Hello"+name+","+message);
    }

    //위의 함수를 호출하는 코드
    sayHi("Dami","how are you today?");

  ```
  - 함수는 return 문을 만나는 즉시 실행을 멈추고 빠져나온다. return 문 뒤의 코드는 결코 실행되지 않는다.
  ```
    function sum(num1, num2){
      return num1 + num2;
      alert("Hello world");
    }

    var result = sum(5, 10); // 결코 실행되지 않는다
  ```
  - 매개변수 어렵다. //도움
  - 오버로딩 없음: 같은 이름으로 함수를 여러 번 정의하면 마지막 함수가 해당 이름을 소유한다.
    ```
      function addSomeNumber(num){
        return num + 100;
      }

      function addSomeNumber(num){
        return num + 200;
      }

      var result = addSomeNumber(100); // 300

    ```