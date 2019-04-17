# Property: box-sizing

- 2019.04.17: 첫 작성

## box-sizing

- Box의 크기를 화면에 표시하는 방식을 변경하는 속성
- width, height 크기가 적용되는 box 설정

| 속성값                          | 설명                                                          |
| ------------------------------- | ------------------------------------------------------------- |
| content-box                     | Default<br>content 만 box 로 설정<br>border 와 padding 미포함 |
| border-box                      | content, border, padding 을 모두 포함하여 box 설정            |
| [initial](./Keyword_initial.md) | 초기 설정 유지                                                |
| [inherit](./Keyword_inherit.md) | 부모 element 설정 상속                                        |

- 예시: border-box 와 content-box 의 차이
  ![Difference of border-box and content-box](https://s3-ap-northeast-2.amazonaws.com/opentutorials-user-file/module/2367/4707.jpeg)

## 출처

- [생활코딩 CSS 수업 - box-sizing](https://opentutorials.org/course/2418/13405)
- [W3SCHOOL - CSS box-sizing Property](https://www.w3schools.com/cssref/css3_pr_box-sizing.asp)
