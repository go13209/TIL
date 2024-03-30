# MongoDB

- 데이터베이스의 정의와 사용 이유
  - 정의
    - 여러 사람이 공유하여 사용할 목적으로 체계화해 통합, 관리하는 데이터의 집합
  - 사용 이유
    - 데이터를 효율적으로 저장하고 압축하여 관리하기 쉽고 접속하기 쉽게 만들어 준다.
    - 데이터를 쉽게 추가,삭제, 수정할 수 있으며, 데이터를 필터링, 정렬하고 검색할 수 있다.
    - 보안 및 관리자 제어 등의 추가 기능을 제공하여 대규모 앱이나 팀에 유용하고 효율적이다.
- 데이터베이스의 종류
  - SQL (Structured Query Language)
    - 구조화된 쿼리 언어, 즉 기본적인 구문을 공유하는 관계형 데이터베이스
    - 정해진 스키마와 테이블에 따라 데이터 저장
    - 관계를 통해 여러 테이블에 데이터 분산 저장
    - 종류: MySQL, Postgres, SQLite, Oracle, Microsoft SQL Server
  - NoSQL
    - SQL의 구조화된 쿼리 언어를 사용하지 않고, 많은 요소를 포괄하는 방식
    - 스키마, 관계 없음
    - 종류: MongoDB, CouchDB, Neo4j, Cassandra, Redis
- 기본 구문
  - MongoDB는 내부적으로 데이터를 BSON 형식으로 저장
    - BSON은 JSON과 동일한 구조지만 Binary 형태로 변경된 구조
    - BSON은 JSON보다 메모리 사용에 효율적이며 보다 빠르고 가볍고 유연함
  - 데이터베이스 생성
    ```jsx
    use + 데이터베이스 이름
    ```
  - 데이터 삽입
    - 단일 데이터 삽입
      ```jsx
      db.collection.insertOne();
      ```
    - 다수 데이터 삽입
      ```jsx
      db.collection.insertMany();
      ```
    - 데이터를 삽입할 집합(collection)을 지정해야 하며, 지정한 이름의 집합이 존재하지 않으면 자동 생성함
  - 데이터 검색
    - 쿼리를 충족하는 모든 데이터 반환
      ```jsx
      db.collection.find( <query>, <projection>, <options> )
      ```
    - 쿼리를 충족하는 첫 번째 데이터 반환
      ```jsx
      db.collection.findOne( <query>, <projection>, <options> )
      ```
    - 중첩된 특성을 찾으려면 따옴표를 쓰고 마침표 구문을 써야 한다.
  - 데이터 수정
    - 필터와 일치하는 첫 번째 데이터 수정
      ```jsx
      db.collection.updateOne( <filter>, <update>, <options> )
      ```
    - 필터와 일치하는 다수 데이터 수정
      ```jsx
      db.collection.updateMany( <filter>, <update>, <options> )
      ```
    - 필터와 일치하는 첫 번째 데이터를 교체
      ```jsx
      db.collection.replaceOne( <filter>, <replacement>, <options>)
      ```
    - 업데이트 연산자 표현식을 사용하여 데이터 수정
      - $set : 필드의 값을 새로운 값으로 대체할 때 사용하며 존재하지 않는 필드-값 입력 시 해당 필드 추가
        ```jsx
        { $set: { <field1>: <value1>, ... } }
        ```
      - $currentDate : 필드의 값을 현재 날짜(날짜 또는 타임스탬프)로 설정
        ```jsx
        { $currentDate: { <field1>: <typeSpecification1>, ... } }
        ```
        - 필드 값을  `true` 로 설정하거나 유형을 명시적으로 지정하는 문서 `{ $type: "timestamp" }` 또는 `{ $type: "date" }` 를 사용해 필드 값을 현재 날짜로 설정
  - 데이터 삭제
    - 필터와 일치하는 첫 번째 데이터 삭제
      ```jsx
      db.collection.deleteOne();
      ```
    - 필터와 일치하는 모든 데이터 삭제
      ```jsx
      db.collection.deleteMany();
      ```
  - MongoDB 내장 연산자
    - 비교 연산자
      | 이름 | 설명 |
      | ---- | -------------------------------------------------------------- |
      | $eq | 해당 값과 일치하는 값을 가진 데이터를 찾는다. |
      | $gt | 해당 값보다 더 큰 값을 가진 데이터를 찾는다. |
      | $gte | 해당 값보다 크거나 같은 값을 가진 데이터를 찾는다. |
      | $lt | 해당 값보다 작은 값을 가진 데이터를 찾는다. |
      | $lte | 해당 값보다 작거나 같은 값을 가진 데이터를 찾는다. |
      | $ne | 해당 값과 일치하지 않는 값을 가진 데이터를 찾는다. |
      | $in | 필드의 값이 배열 안에 들어있는 값들 중 하나인 데이터를 찾는다. |
      | $nin | 필드의 값이 배열 안의 값들이 아닌 데이터를 찾는다. |
    - 논리 연산자
      | 이름 | 설명 |
      | ---- | ----------------------------------------------------------- |
      | $and | 여러 개의 조건을 모두 만족하는 데이터를 찾는다. |
      | $not | 뒤의 조건을 만족하지 않는 데이터를 찾는다. |
      | $nor | 여러 개의 조건을 모두 만족하지 않는 데이터를 찾는다. |
      | $or | 여러 개의 조건 중에 적어도 하나를 만족하는 데이터를 찾는다. |
