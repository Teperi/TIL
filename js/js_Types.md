# JavaScript Types

- 2019.04.03: 첫 작성

## Types

- JS 는 Dynamic 언어이다.
  - type을 미리 선언할 필요 없음
  - Primitive values 는 변경이 불가능(immutable value)하다.
    - 보통의 경우 Object 화 되어 처리됨

|   Types   | 설명   | 특징                                                                                                                                                                                                                                              | 비고                                                                                                                    |
| :-------: | :--- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-------------------------------------------------------------------------------------------------------------------- |
|  Number   | 숫자형  | 정수,소수 모두 아우를 수 있음                                                                                                                                                                                                                               | - *null* 이나 *''* 은 ***0*** 으로 인식<br> - *String* 은 ***NaN*** 으로 인식 <br> (NaN 은 == 비교시 무조건 False 를 반환 / 비교시 isNaN() 사용) |
|  String   | 문자열  | [primitive string 과 string object 를 다르게 취급](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String#%EB%AC%B8%EC%9E%90%EC%97%B4_%EC%9B%90%ED%98%95%EA%B3%BC_String_%EA%B0%9D%EC%B2%B4%EC%9D%98_%EC%B0%A8%EC%9D%B4) | - 큰따옴표와 작은따옴표의 차이 없음 <br> - Literals 와 Escape notation 허용                                                             |
|  Boolean  | 불리언  | Object 와 Primitive value 를 똑같이 사용할 수 없음                                                                                                                                                                                                         | - 값이 없거나, 0, -0, null, false, NaN, undefined, "" => false <br> - 그외 모두 true ("false" 도 Boolean 은 true 가 됨)            |
|  Symbol   | 심볼   | ES6 에서 새로 추가된 속성                                                                                                                                                                                                                                | - 내장 객체 속성과의 충돌을 피해줌 <br> - [for ... in 에서 건너뜀](https://javascript.info/symbol#symbols-are-skipped-by-for-in)         |
|  Object   | 객체   | name - value pairs 모음                                                                                                                                                                                                                           | - Function, Array, Date, RegExp 가 모두 객체                                                                               |
|   Null    |      | 어떤 값이 의도적으로 비어있는 경우                                                                                                                                                                                                                             |                                                                                                                       |
| Undefined |      | 어떤 값이 정의되지 않은 경우                                                                                                                                                                                                                                |                                                                                                                       |

## 출처

- [MDN: JavaScript 재입문하기](https://developer.mozilla.org/ko/docs/A_re-introduction_to_JavaScript)
- [[JavaScript] 자바스크립트의 숫자 타입](https://d2fault.github.io/2018/02/28/20180228-javascript-number-type/)
- [MDN: 자바스크립트의 자료형](https://developer.mozilla.org/ko/docs/Web/JavaScript/Data_structures)
- [책: 만들면서 이해하는 ECMAScript 6](https://www.aladin.co.kr/shop/wproduct.aspx?ItemId=146577348)