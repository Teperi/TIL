# ReactJS Web Service

## 강의 링크

[ReactJS로 웹 서비스 만들기](https://academy.nomadcoders.co/p/reactjs-fundamentals)

## 작성 내역

- 2019.02.19 첫 작성
- 2019.03.11 전체 강의내용 정리 및 포멧 수정

## 내용 정리

### ReactJS 특성

- 별도로 다른 프레임워크를 배울 필요 없이 JS 만 잘 알고 있으면 충분히 사용 가능
- Composition
  - 구조를 요소별, 컴포넌트별로 나눠서 작업 가능
- Undiretional Dataflow
  - 단방향 데이터플로우: Data changes UI
- 프레임워크가 아닌 UI 라이브러리 임.
- MVC 패턴에서 ReactJS 는 View 에 해당함. 따라서 M / C 부분에는 다른 것을 가져다 사용할 수 있음

### 트랜스파일러(transpiler) / 크로스 컴파일러

- 특정 언어로 작성된 프로그램을 다른 언어에서 실행되도록 변환
- JS 코드를 브라우저가 이해할 수 있는 언어로 변환시켜줌
  - 브라우저가 ES6 을 지원하지 못할 때 유용함
  ![WebPack](../Images/webpack.jpg)
  *출처:* [*webpack 공식 사이트*](https://webpack.js.org/)

### JSX

- React Component 를 만들 때 사용하는 언어

### Props

- 부모 Component 에서 자식 Component 로 데이터를 전달할 때 사용
- props 가 Object 형태로 전달됨
- Main Component 가 모든 Data 를 가지고 있고, 자식에게 Props 로 전달해서 사용 가능함

### state

- React Component 안에 있는 Object
- State 가 바뀔 때마다 Render 가 재실행된다
- State 를 바꿀 때는 직접 접근하면 안됨 : setState 를 사용해서 변경해야 함
- state 와 componentDidMount를 같이 사용하면 infinite scroll 같은 것도 만들 수 있음
  - 기존 데이터에 합쳐서 추가할 땐 아래 코드 필요함

  ```js
  ...this.state
  // ... : Spread Oprator
  // 한번에 모든 값들을 집어넣게 함
  // https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Spread_syntax
  ```

- Loading State
  - API 에서 정보를 받아와서 state 를 업데이트 하려면 사용
