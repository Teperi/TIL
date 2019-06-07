# Fragment

- 2019.06.07: 첫 작성

## <React.Fragment>

- React component에서 여러개의 element 를 보내고 싶을 때 사용
  - return 시 element 를 1개 사용해야 함 ▶ 이로 인해 의미없는 div 생성
  - 위와 같은 상황을 막고자 Fragment API 제공

  - 사용법

  ```JSX
  class Columns extends React.Component {
    render() {
      return (
        <React.Fragment>
          <td>Hello</td>
          <td>World</td>
        </React.Fragment>
      );
    }
  }
  ```

## 출처

- [React 공식문서: Fragments](https://reactjs.org/docs/fragments.html)
