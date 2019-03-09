# ReactiveX

- 2019.02.27: 최초 작성
- 혹시나 이 문서를 보게 되신 분들께
  - 이 문서는 매우 틀린 내용을 담고 있을 가능성이 큽니다. 그에 따라 저는 이 글을 신뢰할 수 없음을 알려드립니다.
  - 초보 프로그래머 라서 이 개념을 수정하기 위해 많은 시행착오를 겪을 가능성이 큽니다.

## 내용 정리

> 어떤 개념을 정말로 이해하려면 그 개념이 최초로 언급된 당시의 전후 맥락을 재구성해 볼 필요가 있다. 이렇게 해야 개념의 정수가 그 모든 중간자를 거치고도 살아남았음을 확인할 수 있다.
>
> <프로그래머의 길, 멘토에게 묻다>

### Reactive Programming

- 반응형 프로그래밍

  ```js
  // Imperative(명령형) -> Reactive(반응형)
  b = 27;
  c = 33;
  a = b + c;
  console.log(a) // 60 -> 60
  c = 40;
  console.log(a) // 60 -> 67
  ```

  - Spreadsheet가 반응형의 가장 대표적인 예

- Reactive Programming 의 2가지 키워드
  - **Observable**
    - Observer pattern: 신문 구독 시스템
      - 관찰자가 바뀐 정보를 구독자에게 전달
      - 옵저버 패턴이 바로 반응형 프로그래밍 그 자체
        ![Observer Pattern Example](https://examples.javacodegeeks.com/wp-content/uploads/2018/10/Screen-Shot-2018-10-29-at-8.59.08-PM.jpg)
    - Hot Observable(Eager Evaluation)
      - 구독자가 없어도 이벤트 전달 로직 실행
      - 예시) 스트리밍/방송: 보는 사람이 없어도 방송 실행
    - Cold Observable(Lazy Evaluation)
      - 구독자가 없으면 이벤트 전달 로직 미실행
      - 예시) VOD 서비스: 직접 재생시키기 전까진 재생 안됨

  - **Data Flow**
    - 프로그래밍 로직 짜는 방법이 두가지 있음
      - Control Flow: Goto, if-else, For, While 등등
        - 변수를 변화시켜 로직 전개

        ```js
        let numbers = ['1','2','3','4','5'];
        let numbersLength = numbers.length;

        // 숫자형 변환
        for (let i = 0; i < numbersLength; i++) {
            numbers[i] = parserInt(numbers[i]);
        }
        console.log(numbers); // [1,2,3,4,5]

        // 필터 기능 - 2의 배수인 경우 삭제
        for (let i = 0; i < numbersLength; i++) {
            if(numbers[i]%2 === 0) {
                numbers.splice(i, 1);
            }
        }
        console.log(numbers); // [1,3,5]

        // 나머지 숫자 더하기
        numbersLength = numbers.length;
        let sum = 0;
        for (let i = 0; i < numbersLength; i++) {
            sum += numbers[i];
        }
        console.log(sum) // 9
        ```

      - Data Flow: Stateless, Recursion, Pipe
        - 사람 사이의 모든 의사소통은 이렇게 이루어짐
        - 변수X, 재귀함수 or 파이프 방식으로 로직 전개
        - map, filter, reduce 등

        ```js
        let numbers = ['1','2','3','4','5']

        let sum = numbers.map(item => parserInt(item)) // 숫자형 변환
                         .filter(item => item%2 === 1) // 필터 기능
                         .reduce((a, b) => a + b) // 나머지 숫자 더하기

        console.log(sum) // 9
        ```

        - 반응형 프로그래밍은 함수형 프로그래밍을 활용한다<sup id="sup1">[1](#footnote1)</sup>
          - 우리가 앞으로 볼 Rx 는 FRP(Functional reactive programming) 이라고 불린다.
        - 반응형 프로그래밍은 데이터의 흐름에서 시작된다.<sup id="sup1">[1](#footnote1)</sup>
          - ex: 로그인 화면 데이터 -> ID, 비밀번호
          - ex: 사용자 클릭

### Rx(ReactiveX)

- An API for asynchronous programming with observable streams
  - 비동기 프로그래밍을 가능하게 해주는 API
- Java, JS, Swift 등 지원

- 비동기 프로그래밍 문제 해결 방법
  1. Reactive Programming
     - 외부에서 데이터를 가져와서 목적지까지 운반
  2. LINQ(Language Intergrated Query)
     - 통합 질의 언어
     - SQL 쿼리처럼 표현할 수 있게 도와주는 일종의 확장 문법
     - 쿼리 구문(Query syntax) 과 메소드 구문(Method Syntax) 타입 지원

     ```c#
     //Query syntax:
     IEnumerable<int> numQuery1 =
     from num in numbers
     where num % 2 == 0
     orderby num
     select num;

     //Method syntax:
     IEnumerable<int> numQuery2 = numbers
     .Where(num => num % 2 == 0)
     .OrderBy(n => n);
     ```

     > - ex: 마우스 이동
     >   - 마우스를 움직일 때마다 변하는 현재 위치 좌표는 외부에서 안으로 들어오는 자극이자, 데이터다. 이 좌표 데이터들은 Rx의 Observable이 만들어 놓은 문을 통해 프로그램 안으로 진입한다. 프로그램 안으로 들어온 데이터는 LINQ로 미리 작성해둔 오퍼레이터 사이를 헤엄쳐 최종 목적지에 도달한다. 프로그램은 최종 목적지로 들어온 데이터를 확인하여 응답한다. 이 과정은 마우스가 이동을 멈추지 않는 한 끊임없이 계속해서 이뤄진다. 마치 강물이 흐르듯이. 이게 Rx가 제안하는, 데이터 관점의 비동기 처리 방식이다.<sup id="sup2">[2](#footnote2)</sup>

---

- <b id="footnote1">1</b> : [RxJava #1 반응형 프로그래밍이란 무엇인가?](https://brunch.co.kr/@yudong/33) [↩](#sup1)
- <b id="footnote2">2</b> : [김코딩: MS는 ReactiveX를 왜 만들었을까? (feat. RxJS)](http://huns.me/development/2051) [↩](#sup2)

## 출처

- [Vue.js와 Reactive Programming 자막](https://www.slideshare.net/sunhyouplee/vuejs-reactive-programming-vuetiful-korea-2nd)
- [Reactive Programming With Swift](https://www.slideshare.net/sunhyouplee/reactive-programming-with-swift)
- [김코딩: MS는 ReactiveX를 왜 만들었을까? (feat. RxJS)](http://huns.me/development/2051)
- [[RxSwift] RxSwift란? ReactiveX 란?](https://medium.com/@jang.wangsu/rxswift-rxswift%EB%9E%80-reactivex-%EB%9E%80-b21f75e34c10)

## 수정 공부용 출처

- [NDC14 - Rx와 Functional Reactive Programming으로 고성능 서버 만들기](https://www.slideshare.net/jongwookkim/ndc14-rx-functional-reactive-programming?next_slideshow=1)
- [[Reactive] Reactive Programming 배우는 방법](https://mobicon.tistory.com/467)