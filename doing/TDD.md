# TDD (테스트 주도 개발)

- 2019.03.01: 최초 작성
- 2019.03.02: 1차 정리

> 프로그램을 작성하기 전에 테스트 먼저 하라! (Test the program before you write it.)
> *-Kent Beck-*

## 정리

### 목표

- **잘 동작하는 깔끔한 코드**

### 진행 방식

- 질문(Ask):테스트 작성을 통해 시스템에 질문한다. (테스트 수행 결과는 실패)
- 응답(Respond):테스트를 통과하는 코드를 작성해서 질문에 대답한다. (테스트 성공)
- 정제(Refine): 아이디어를 통합하고, 불필요한 것은 제거하고, 모호한 것은 명확히 해서 대답을 정제한다. (리팩토링)
- 반복(Repeat): 다음 질문을 통해 대화를 계속 진행한다.

> ![TDD Flowchart](https://upload.wikimedia.org/wikipedia/commons/thumb/0/0b/TDD_Global_Lifecycle.png/1920px-TDD_Global_Lifecycle.png)
> [*출처: 영문 위키백과*](https://en.wikipedia.org/wiki/Test-driven_development)

### 규칙

- 오직 자동화된 테스트가 실패할 경우에만 새로운 코드를 작성한다.
- 중복을 제거한다.

## 출처

- [책: 테스트 주도 개발](https://www.aladin.co.kr/shop/wproduct.aspx?ItemId=37469717)
- [책: TDD 실천법과 도구](https://repo.yona.io/doortts/blog/issues)
- ['OKKYCON: 2018 - The Real TDD': TDD 제대로 알기](https://www.samsungsds.com/global/ko/support/insights/OKKYCON-TDD.html)
- [JEST](https://jestjs.io/)
- [김코딩: 도전! JavaScript TDD – 1. 시작](http://huns.me/development/716)
- [김코딩: 3년간의 TDD 인생 회고](http://huns.me/development/2206)
- [블로그: Test-Driven Development](https://soulpark.wordpress.com/2012/09/12/test-driven-development/)