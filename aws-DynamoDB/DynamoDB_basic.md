# DynamoDB 기초

- 2019.03.22: 첫 작성

## NoSQL

- RDBMS(Relational database management system)의 보완재

  - RDBMS: 테이블 사이의 관계가 맺어지는 DB 형태 및 DB 관리 시스템
  - 정형 데이터 관리 용이
  - 성능을 높히기 위해선 Scale Up 이 필요함
    - 확장성이 떨어짐

- NoSQL(Not only SQL)
  - RDBMS 가 못하는 것들을 처리하기 위해서 만들어짐
    - SNS 확산: 비정형 데이터 처리 필요
    - 무선 사용량 및 속도 증가: 응답 및 처리속도 빠르게 해야 함
    - 가격 부담: RDBMS 의 경우 매번 더 좋은 성능을 사용하기 위해서 장비를 더 좋은것을 사용해야 함
    - 여러 문제점들 해결하기 위해 다양한 해결책을 제시
      - 모든 것을 다 처리할 순 없다. trade-off 존재함
        ![PACELC](http://happinessoncode.com/images/cap-theorem-and-pacelc/pacelc.png)
    - _출처: [CAP 이론과 PACELC 이론을 알아보자](http://happinessoncode.com/2017/07/29/cap-theorem-and-pacelc-theorem/)_

## DynamoDB

![aws DynamoDB Logo](https://t1.daumcdn.net/cfile/tistory/2473F94D57EDFFA512)

- Amazon 에서 만든 NoSQL 데이터베이스 서비스
- Key-Value 및 document document data 구조
- 어떤 규모에서도 10밀리초 미만의 성능 제공

### 사용 방법

- nodejs 에서 JSON 파일을 보내는 방식으로 사용 가능
- 테이블 생성 예시

  ```js
  // aws-sdk 불러오기
  var AWS = require("aws-sdk");
  // 설정 확인
  AWS.config.update({
    region: "ap-northeast-2",
    endpoint: "https://dynamodb.ap-northeast-2.amazonaws.com"
  });

  // dynamodb 연결
  var dynamodb = new AWS.DynamoDB();

  // JS 변수 작성
  var params = {
    // 테이블 이름
    TableName: "Movies",
    // 테이블 key 스타일 정의
    KeySchema: [
      { AttributeName: "year", KeyType: "HASH" }, //Partition key
      { AttributeName: "title", KeyType: "RANGE" } //Sort key
    ],
    // 테이블 key 사용 값 정의
    AttributeDefinitions: [
      { AttributeName: "year", AttributeType: "N" },
      { AttributeName: "title", AttributeType: "S" }
    ],
    // 데이터 사용량 정의
    ProvisionedThroughput: {
      ReadCapacityUnits: 10,
      WriteCapacityUnits: 10
    }
  };

  // params를 dynamodb 에 넣기
  dynamodb.createTable(params, function(err, data) {
    if (err) {
      console.error("Unable to create table. Error JSON:", JSON.stringify(err, null, 2));
    } else {
      console.log("Created table. Table description JSON:", JSON.stringify(data, null, 2));
    }
  });
  ```

- [AWS 자습서: Node.js와 DynamoDB](https://docs.aws.amazon.com/ko_kr/amazondynamodb/latest/developerguide/GettingStarted.NodeJs.html) 로 접속하면 CRUD 및 쿼리, 스캔에 대한 설명 및 코드 확인 가능

## 출처

- [WIKIPEDIA: 관계형 데이터베이스 관리 시스템](https://ko.wikipedia.org/wiki/%EA%B4%80%EA%B3%84%ED%98%95_%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4_%EA%B4%80%EB%A6%AC_%EC%8B%9C%EC%8A%A4%ED%85%9C)
- [WIKIPEDIA: NoSQL](https://ko.wikipedia.org/wiki/NoSQL)
- [WIKIPEDIA: Amazon DynamoDB](https://en.wikipedia.org/wiki/Amazon_DynamoDB)
- [AWS 자습서: Node.js와 DynamoDB](https://docs.aws.amazon.com/ko_kr/amazondynamodb/latest/developerguide/GettingStarted.NodeJs.html)
