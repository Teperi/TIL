# REST, RESTful, REST API

- 2019.02.24(최초작성)
- 2019.02.26(1차 정리 및 완성)
- 2019.02.27(제목 수정 및 레이아웃 변경)

![REST](https://t1.daumcdn.net/cfile/tistory/2728BA505940EBDD17)

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

- 왜 REST API 개발자는 현재 REST 가 잘못되었다고 말하는가?

### REST(REpresentational State Transfer)

- 영어 직역: 대표적인 상태 전달
  - 자원의 대표에 의한 상태 전달<sup id="sup2">[2](#footnote2)</sup>
    - 자원의 대표
      - 자원: 해당 소프트웨어가 관리하는 모든 것
      - 대표: 자원을 특정할 수 있는 값(id 등)
    - 상태 전달
      - 데이터를 요청하는 시점의 자원의 상태(정보) 전달
    - *HTTP 를 통해 CRUD 를 실행할 수 있는 API를 REST 라고도 부름*
      - *위 이야기 덕분에 REST 에 대해 어렵게 되기도 함*

- 분산 하이퍼미디어 시스템(like web)을 위한 아키텍쳐 스타일
  - 아키텍쳐 스타일: 제약조건들의 집합
  
- REST 구성 스타일
  - **아래 스타일을 다 맞춘 서비스를 RESTful 하다고 이야기 함**
  - Uniform Interface 를 제외한 나머지 부분은 HTTP 만 제대로 따르면 잘 지킬 수 있다.<sup id="sup3">[3](#footnote3)</sup>
  - Client-Server: 각각의 역할이 확실히 구분되어야 함
    - Server: API 제공, 비즈니스 로직 처리 및 저장 관리
    - Client: 사용자 인증이나 컨텍스트(세션, 로그인 정보)등 관리
  - Stateless: 무상태성 / 작업을 위한 상태정보(세션, 쿠키 등)를 따로 저장 및 관리하지 않음
    - Client가 요청한 작업내역을 Server에 저장하지 않음
    - Server는 들어오는 요청만을 단순히 처리
  - Cacheable: 대량의 요청을 효율적으로 처리하기 위해 캐시 처리 가능
  - Layered System: 계층화 / Server를 다중 계층으로 구성될 수 있음
    - 보안, 로드밸런싱, 암호화, 사용자 인증 등 추가 가능
    - 구조상의 유연성 확보 및 보안성 향상 가능
  - Code-On-Demand(Optional)
    - Server로부터 스크립트를 받아서 Client에서 실행
      - ex)JavaScript
    - 반드시 충족할 필요 없음
  - Uniform Interface: 인터페이스 일관성
    - identification of resources
      - URI 가 식별되어야 함 / 잘 지켜지고 있음
    - manipulation of resources through representations
      - CRUD 시에 HTTP 메시지에 내용을 담아서 전송 / 잘 지켜지고 있음
    - self-descriptive messages
      - 메시지는 스스로를 설명해야한다
      - 확장 가능한 커뮤니케이션

      ```JSON
      GET / HTTP/1.1   <!-- X: 스스로가 어디서 왔는지 설명하지 않음 -->

      GET / HTTP/1.1
      Host: www.example.org   <!-- O: 이렇게 주소 써줘야 함 -->
      ```

      ```JSON
      HTTP/1.1 200 OK

      [ { "op": "remove", "path": "/a/b/c" } ]
        <!-- X: 이것이 어떤 문법으로 쓰여졌는지 설명할 수 없음 -->

      HTTP/1.1 200 OK
      Content - Type: application/json-patch+json

      [ { "op": "remove", "path": "/a/b/c" } ]
        <!-- O: 명세를 찾아서 해석이 가능하도록 제대로 주어야 함 -->
        <!-- application/json 으로는 부족함. op 가 무엇인지 모름 -->
      ```

    - hypermedia as the engine of application state (HATEOAS)
      - 애플리케이션의 상태는 Hyperlink 를 이용해 전이되어야 한다.
      - 링크는 동적으로 변경될 수 있다.
      - 아래 예시는 모두 올바른 예시

      ```HTML
      <a href="/test">test</a>
      ```

      ```JSON
      HTTP/1.1 200 OK
      Content-Type: aplication/json
      Link: </articles/1>; rel="previous",
            </articles/3>; rel="next;
      {
        "title": "The second article",
        "contents": "blah blah..."
      }
      ```

- REST 구성 요소
  - Resource(자원): 접근할 대상
    - 모든 자원에 고유ID 존재, Server 내 존재함
    - HTTP: URI
  - Method(Verb, 행위): 할일(CRUD)
    - HTTP: Get, Post, Put, Delete
  - Representation of Resource: 표현(메시지)
    - Client 의 요청에 따른 Server 의 응답
    - JSON 및 XML 으로 데이터를 일반적으로 주고받음

### 독립적 진화

- Uniform Interface 가 지켜져야 하는 이유
  - REST를 만들게 된 계기: [**"How do I improve HTTP without breaking the Web."**](https://www.infoq.com/articles/roy-fielding-on-versioning)
- Server 와 Client 가 각각 독립적으로 진화
- Server 의 기능이 변경되어도 Client 를 업데이트할 필요가 없다.

- **Web**: REST 가 잘 지켜지는 사례
  - 웹 페이지가 변경되었다고 해서 웹 브라우저를 업데이트할 필요 없음
  - 웹 브라우저를 업데이트했다고 웹 페이지를 변경할 필요 없음
    - 비교: 앱은 강제업데이트 한 후에 동작하는 경우 생김
  - HTTP 및 HTML 명세가 변경되어도 웹을 잘 동작함
  - 수많은 사람들의 노력 덕분
    - W3C / IETF / 웹 서버 및 브라우저 개발자들
    - 상호운용성(Interoperability)에 대한 집착

- REST 가 웹의 독립적 진화에 도움이 됨
  - HTTP 에 지속적 영향
  - Host 헤더 추가
  - 414 URI Too Long 등

### REST API

- API: Application Programming Interface
  - 서로 정보를 교환가능 하도록 하는 것
- REST API
  - REST 기반으로 서비스 API 를 구현한 것
  - [마이크로소프트 REST API 가이드라인](https://docs.microsoft.com/ko-kr/azure/architecture/best-practices/api-design)
    - 완전히 RESTful 한것은 아니나, 충분히 통용 가능한 가이드라인

- 웹과 REST API 차이

| 비교         | 웹 페이지 | HTTP API  |
| ---------- | ----- | --------- |
| Protocol   | HTTP  | HTTP      |
| 커뮤니케이션     | 사람-기계 | **기계-기계** |
| Media Type | HTML  | **JSON**  |

- JSON 에서 의미 해석을 하려면 별도의 문서가 필요함
  - Self-descriptive
    - 방법1: Media Type(IANA 에 미디어타입의 명세 등록)
    - 방법2: Profile(명세를 작성해서 Link 헤더에 해당 명세 링크)
  - HATEOAS
    - 방법1: Data 내에 하이퍼링크 표현
    - 방법2: HTTP 헤더 사용

---

- <b id="footnote1">1</b> : [고려대학교: CMS홈페이지 개요](https://kucms.korea.ac.kr/kucms/about/summary.do) [↩](#sup1)
- <b id="footnote2">2</b> : [REST와 RESTful API](https://www.a-mean-blog.com/ko/blog/%ED%86%A0%EB%A7%89%EA%B8%80/_/REST%EC%99%80-RESTful-API) [↩](#sup2)
- <b id="footnote3">3</b> : [그런 REST API 로 괜찮은가](https://youtu.be/RP_f5dMoHFc?t=638) [↩](#sup3)

## 정리 출처

- [그런 REST API 로 괜찮은가](https://youtu.be/RP_f5dMoHFc)
  - [발표 슬라이드](https://slides.com/eungjun/rest#/)

- 참고 자료들(실제 API 작성 방식도 같이 들어있음)
  - [TOAST: REST API 제대로 알고 사용하기](https://meetup.toast.com/posts/92)
  - [DEVGEAR: REST API 이해하기](http://tech.devgear.co.kr/delphi_news/433404)
  - [REST란? REST API란? RESTful이란?](https://gmlwjd9405.github.io/2018/09/21/rest-and-restful.html)
  - [RESTFul이란 무엇인가?](https://blog.remotty.com/blog/2014/01/28/lets-study-rest/)
  - [SPOQA: REST 아키텍처를 훌륭하게 적용하기 위한 몇 가지 디자인 팁](https://spoqa.github.io/2012/02/27/rest-introduction.html)