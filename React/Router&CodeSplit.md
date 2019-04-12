# React Router & Code Split

- 2019.04.12: 첫 작성

## Routing

- 출발지에서 목적지까지의 경로를 결정하는 기능
  - 앱에서의 Routing: view 전환 네이베이션 관리 기능
  - URL 입력, a 링크 클릭, history.back 등
- react-router: Routing 을 간단하게 해 주는 라이브러리

## Code Splitting

- SPA: Page 가 1개인 앱
  - 서버로부터 새로운 페이지를 불러오지 않고 현재의 페이지를 동적으로 다시 작성함으로써 사용자와 소통하는 웹 앱 또는 웹사이트
  - 장점
    - 연속되는 페이지들 간의 사용자 경험의 간섭을 막아줌
    - 웹이 네이티브 앱과 유사하게 동작하도록 만들어줌
    - 브라우저에서 구동시킨 후 필요한 데이터만 바뀌는 방식이어서 데이터를 줄일 수 있음
  - 단점
    - 앱의 규모가 커지면 자바스크립트 파일 사이즈가 너무 커짐
      - 초기 구동 속도가 느려지고, 트래픽이 늘어남
      - Code Splitting 으로 해결 가능
    - SEO 문제
      - 자바스크립트 기반 비동기 모델이라서 검색엔진이 정보를 확인할 수 없음
      - 대응 기술이 있음 - 선별적 SEO 대응 가능(추후 공부 할 예정)
- **필요한 Code 만 불러오도록 해서 로딩 속도를 빠르게 만드는 것이 Splitting 의 목적**

## 예제 작업

1. 터미널 작업

   - create-react-app 으로 프로젝트 생성
   - yarn add react-router-dom

2. App.js 변경

   - 전체 삭제 이후 rafc 로 새로 생성
   - _App.js_

   ```JSX
   import React from 'react';
   import {BrowserRouter as Router, Route} from 'react-router-dom'

   const App = () => {
     return (
         <div>
          test
         </div>
     );
   };

   export default App;
   ```

3. Home, About 생성

   - src 내 routes 폴더 생성
   - Home.js, About.js 생성: 각각 페이지 구분 용으로 글만 써두기

4. App.js Route 추가

   - _App.js 변경_

   ```JSX
   import React from 'react';
   import { BrowserRouter as Router, Route } from 'react-router-dom';

   import Home from './routes/Home';
   import About from './routes/About';
   import Header from './components/Header';

   const App = () => {
     return (
       <Router>
         <div>
           <Header />
           <Route exact path='/' component={Home} />
           <Route path='/about' component={About} />
         </div>
       </Router>
     );
   };

   export default App;
   ```

5. NavLink 사용

   - Components 폴더 생성
   - _Header.js_

   ```JSX
   import React from 'react';
   import './Header.css';
   import { NavLink } from 'react-router-dom';

   const Header = () => {
     return (
       <div className='header'>
         <NavLink exact to='/' className='item'>
           홈
         </NavLink>
         <NavLink to='/about' className='item'>
           소개
         </NavLink>
       </div>
     );
   };

   export default Header;
   ```

   - _Header.css_

   ```CSS
   .header {
     background: #5c7cfa;
     display: table;
     table-layout: fixed;
     width: 100%;
   }

   .item {
     text-align: center;
     padding-top: 1rem;
     padding-bottom: 1rem;
     display: table-cell;
     color: white;
     text-decoration: none;
     font-size: 1.1rem;
   }

   .item:hover {
     background: #748ffc;
   }

   .item:active,
   .item.active {
     background: white;
     color: #5c7cfa;
   }
   ```

6. 코드 스플리팅

   - _SplitMe.js_

   ```JSX
   import React from 'react';

   const SplitMe = () => {
     return <div>클릭할때만 로딩시켜줘</div>;
   };

   export default SplitMe;
   ```

   - _About.js 버튼 생성_

   ```JSX
   import React, { Component } from 'react';

   import SplitMe from './SplitMe';

   export class About extends Component {
     state = { Split: null };
     handleClick = () => {
       this.setState({
         Split: SplitMe
       });
     };
     render() {
       const { Split } = this.state;
       return (
         <div>
           About
           <button onClick={this.handleClick}>Click Me</button>
           {Split && <SplitMe />}
         </div>
       );
     }
   }

   export default About;
   ```

   - _Network 에서 변경 안되는것 확인 후 About.js 변경_

   ```JSX
   import React, { Component } from 'react';

   export class About extends Component {
     state = { Split: null };
     handleClick = () => {
       import('./SplitMe').then(({ default: SplitMe }) => {
         this.setState({
           Split: SplitMe
         });
       });
     };
     render() {
       const { Split } = this.state;
       return (
         <div>
           About
           <button onClick={this.handleClick}>Click Me</button>
           {Split && <Split />}
         </div>
       );
     }
   }

   export default About;
   ```

## 출처

- [Velopert.LOG: react-router :: 1장. 리액트 라우터 사용해보기](https://velopert.com/3417)
- [Velopert.LOG: [Video] 리액트 라우터 (react-router v4) 강의 [1/3] : 사용 방법](https://velopert.com/3275)
- [Velopert: 리액트 프로젝트 코드 스플리팅 정복하기](https://velog.io/@velopert/react-code-splitting)
