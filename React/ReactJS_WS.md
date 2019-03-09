# ReactJS Web Service

## 강의 링크

[ReactJS로 웹 서비스 만들기](https://academy.nomadcoders.co/p/reactjs-fundamentals)

## 작성 내역

- 2019.02.19 첫 작성

## 내용 정리

- 윈도우에 우분투 설치: Windows Subsystem for Linux<sup id="sup1">[*1*](#footnote1)</sup>
- 만약 Subsystem 이 되지 않을 경우: [블로그 참조](https://webnautes.tistory.com/1170)

- ReactJS 특성
  - 별도로 다른 프레임워크를 배울 필요 없이 JS 만 잘 알고 있으면 사용 가능
  - Composition
    - 구조를 요소별, 컴포넌트별로 나눠서 작업 가능
  - Undiretional Dataflow
    - 단방향 데이터플로우: Data changes UI
  - 프레임워크가 아닌 UI 라이브러리 임.
  - MVC 패턴에서 ReactJS 는 View 에 해당함. 따라서 M / C 부분에는 다른 것을 가져다 사용할 수 있음

- 트랜스파일러(transpiler) / 크로스 컴파일러
  - 특정 언어로 작성된 프로그램을 다른 언어에서 실행되도록 변환
  - JS 코드를 브라우저가 이해할 수 있는 언어로 변환시켜줌
    - 브라우저가 ES6 을 지원하지 못할 때 유용함
  - 강의에서는 Create React App을 사용해서 webpack 을 자동 실행
  ![WebPack](../Images/webpack.jpg)
  *출처:* [*webpack 공식 사이트*](https://webpack.js.org/)

## 출처

<b id="footnote1">1</b> : [윈도우 10에서 Bash shell 지원](https://blogs.msdn.microsoft.com/eva/?p=7633) [↩](#sup1)