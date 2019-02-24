# REST API

2019.02.24(최초정리)

## 정리 출처

- [그런 REST API 로 괜찮은가](https://youtu.be/RP_f5dMoHFc)
  - [발표 슬라이드](https://slides.com/eungjun/rest#/)

## 내용 정리

### 역사 확인

- WEB(1991)
  - 인터넷 정보 공유 방식: HyperText 로 연결
    - 표현 형식: HTML
    - 식별자: URI
    - 전송 방법: HTTP

  - HTTP/1.0 (1994-1996)
    - Roy T.Fielding: "How do I improve HTTP without breaking the Web?"
    - 해결책: HTTP Object Model -> 이후 REST란 이름으로 발표됨(2000년 박사 논문)

- API
  - XML-RPC(1998) -> SOAP(이름 변경)
    - 원격으로 다른 시스템의 메소드 호출 가능한 프로토콜
  - flickr API(2004.8)
    - 여러 형태로 만들어냄: SOAP, REST..
    - SOAP 보다 적은 규칙으로 사용하기 쉬운 REST가 많이 사용됨

- CMIS(2008)
  - Content Management Interoperability Services
  - CMS를 위한 표준
    - CMS: 공공기관, 기업, 대학, 단체 및 협회의 사이트에서 여러개의 서브 사이트를 보유하고 관리 할 때 손쉽게 제작, 관리를 할 수 있는 웹 사이트 분양 솔루션으로써 전문적인 지식이 없어도 웹 사이트 운영 관리자가 손쉽게 운영, 관리할 수 있는 툴을 제공<sup id="sup1">[1](#footnote1)</sup>
  - **REST 바인딩 지원**
    - *Fielding: No REST in CMIS*

- Microsoft REST API Guidelines(2016)
  - 사람들이 생각하는 REST API 에 대한 자세한 가이드라인 제시
    - *Fielding: perl -e 's/REST API/HTTP API/g;'*

왜 REST API 개발자는 현재 REST 가 잘못되었다고 말하는가?

### REST(REpresentational State Transfer) API

- REST 아키텍쳐 스타일을 따르는 API
  - REST: 분산 하이퍼미디어 시스템(like web)을 위한 아키텍쳐 스타일
    - 아키텍쳐 스타일: 제약조건들의 집합
  - REST 구성 스타일 6가지
    - 

---
<b id="footnote1">1</b> : [고려대학교: CMS홈페이지 개요](https://kucms.korea.ac.kr/kucms/about/summary.do) [↩](#sup1)


## 이후 작성해야 할 사항 및 방향

- REST 에 대한 간단한 소개
- REST 와 HTTP 의 비교? 서로 비슷하면서 다르기도 한 부분이 있음
- REST 와 RESTful 의 차이
- REST API 특징 및 규칙

- 참고 자료들
  - [REST란? REST API란? RESTful이란?](https://gmlwjd9405.github.io/2018/09/21/rest-and-restful.html)
  - [REST API 제대로 알고 사용하기](https://meetup.toast.com/posts/92)
  - [RESTFul이란 무엇인가?](https://blog.remotty.com/blog/2014/01/28/lets-study-rest/)
  - [REST 아키텍처를 훌륭하게 적용하기 위한 몇 가지 디자인 팁](https://spoqa.github.io/2012/02/27/rest-introduction.html)
  - [조대협: REST API의 이해와 설계-#1 개념 소개](https://bcho.tistory.com/953)
  - [REST와 RESTful API](https://www.a-mean-blog.com/ko/blog/%ED%86%A0%EB%A7%89%EA%B8%80/_/REST%EC%99%80-RESTful-API)
  