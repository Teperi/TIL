# Vanilla JS

2019.02.13

## 내용 정리

- ECMAScript : 일종의 Specification
  - 각 브라우져들은 이 스펙을 적절히 구현해야 함
  - 현재 ES2016 까지는 왠만큼 구현이 되어 있음
- JavaScript(Vanilla JS): 모든 브라우저에서 사용 가능한 언어
  - jquery 로 작성한 코드를 웹 브라우저에서 실행할 경우, 기본적으로 브라우저에서 JS 로 컴파일해서 사용함
  - JS 가 가장 빠를 수 밖에 없음
  ![JS Compare](../Images/vanillajs_compare.jpg)
  *출처 : [Vanilla-JS](http://vanilla-js.com/)*
  - 따라서 JS 를 배우는 것이 좋음

- 모든 언어는 문법과 규칙이 있음

- let : 변수 선언
- const : Constant, 상수 선언
  - 첫번째 값을 넣을때만 값이 들어감
  - const 선언된 변수를 바꾸려고 하면 에러 생성됨

- JS Data Type
  - String
  - Boolean
  - Number
  - Float

- Array & Object
  - JS Array: [] (bracket / Square brackets)
    - key 값이 각 자리마다 숫자로 저장
    - 리스트 형태로 저장할 자료에 유리함
  - JS Object: {} (Curly barckets)
    - lable:value 형태로 저장
    - Object.lable 로 불러올 수 있음
    - const 로 선언할 경우 각각의 value 는 변경 가능 / object 자체를 변경할 수 없음