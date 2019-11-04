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

- 데이터타입
- 연산자
- 문장
- 함수
