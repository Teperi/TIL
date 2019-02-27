# ReactiveX

- 2019.02.27: 최초 작성

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

---

- <b id="footnote1">1</b> : [RxJava #1 반응형 프로그래밍이란 무엇인가?](https://brunch.co.kr/@yudong/33) [↩](#sup1)

## 출처

- [Vue.js와 Reactive Programming 자막](https://www.slideshare.net/sunhyouplee/vuejs-reactive-programming-vuetiful-korea-2nd)
- [Reactive Programming With Swift](https://www.slideshare.net/sunhyouplee/reactive-programming-with-swift)
- [김코딩: MS는 ReactiveX를 왜 만들었을까? (feat. RxJS)](http://huns.me/development/2051)
- [[RxSwift] RxSwift란? ReactiveX 란?](https://medium.com/@jang.wangsu/rxswift-rxswift%EB%9E%80-reactivex-%EB%9E%80-b21f75e34c10)