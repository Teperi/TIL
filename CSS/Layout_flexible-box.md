# LAYOUT: Flexible Box

- 2019.04.17: 첫 작성
- 2019.04.18: 내용 추가

## CSS Layout 발전 과정

### Table

- 문제1: 이 table이 자료에 대한 표로 만들어졌는지 단순 layout 을 위한 사용인지 확인하기 어려워짐.
- 문제2: table 유지 보수가 어려움(코드가 길어짐)

### position

- table 을 벗어나기 위한 시도 1

### float

- table 을 벗어나기 위한 시도 2
  - 이해하기가 어렵고, 레이아웃을 위한 것이 아니었음

### flex

- container - item 으로 부모 자식 관계
  - 각각 속성이 구분되어 있음
  - 꼭 container - item 으로 이름을 지어줘야 하는 것은 아님

## flexbox

[속성 예제](https://codepen.io/enxaneta/pen/adLPwv)

### container

- display:flex 로 사용 시작
- flex-direction: 정렬 방법 선택
  - Default: row
  - row / column 및 reverse 사용 가능

### item

- flex-basis: 아이템 크기 지정(container 에서 지정한 방향에 따라 달라짐)
  - 브라우저를 작게 만들 경우 설정한 크기보다 줄어듬
- flex-grow: weight 부여, 여백을 모두 차지하도록 함
  - Default: 0
- flex-shrink: 브라우저가 줄어들었을때 크기가 줄어드는 정도 설정
  - 0: 브라우저가 줄어들어도 절대 줄어들지 않는다
  - 양수값으로만 사용 가능

## Holy Grail layout

- 사람들이 웹 페이지를 만들때 흔히 쓰는 레이아웃
- 과거에 이 디자인을 하기 위해 여러 구현 방법들이 있었으나, 모두 단점이 존재했음
  - 그래서 올바른 답을 모르기 때문에 성배를 찾는 과정이라는 생각으로 이름이 붙음
- 현재 flexbox 나 grid layout 으로 손쉽게 해결 가능해짐
  ![Holy grail layout image](https://upload.wikimedia.org/wikipedia/commons/thumb/a/ad/HolyGrail.svg/1280px-HolyGrail.svg.png)
  - 출처: [Wikipedia: Holy grail(web design)](<https://en.wikipedia.org/wiki/Holy_grail_(web_design)>)

## 출처

- [생활코딩 CSS 수업](https://opentutorials.org/course/2418/13339)
- [MDN: CSS Flexible Box Layout](https://developer.mozilla.org/ko/docs/Web/CSS/CSS_Flexible_Box_Layout)
- [NAVER D2: flexbox로 만들 수 있는 10가지 레이아웃](https://d2.naver.com/helloworld/8540176)
