# Styled-jsx

- 2019.07.19: 첫 작성

## 목적

- Next.js 에서 사용하는 Styled-jsx 에 대한 이해

## CSS in JS

- Component 단위의 CSS 관리방식
  - 웹사이트를 SPA 방식으로 개발함에 따라 Component 기반의 CSS 관리가 필요해짐
  - state에 따른 css 변경(Dynamic style) 가능 등의 이점이 있음

## Styled-jsx

- Next.js 설치시 같이 설치되는 framework
  - CSS 를 컴포넌트 내에 작성할 수 있게 도와주는 툴
  - 기본적으로 CSS와 사용법이 같음
  - Dynamic styles, Server-side Rendering 등의 기능 지원
  
- 예시
```JSX
function Home() {
  return (
    <div className="container">
      <h1>Hello Next.js</h1>
      <p>Let's explore different ways to style Next.js apps</p>
      <style jsx>{`
        .container {
          margin: 50px;
        }
        p {
          color: blue;
        }
      `}</style>
    </div>
  )
}

export default Home
```


## 출처

- [잡다한 개발 블로그: [번역]CSS-in-JS에 관해 알아야 할 모든 것](https://d0gf00t.tistory.com/22)
- [Nextjs.org: Styling Next.js with Styled JSX](https://nextjs.org/blog/styling-next-with-styled-jsx)
- [npmjs.com: styled-jsx](https://www.npmjs.com/package/styled-jsx)