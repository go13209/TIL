# ⭐ SQL 심화

## 💡 트랜잭션(Transactions)

- 여러 쿼리문을 묶어서 하나의 작업처럼 처리하는 방법
- 쪼개질 수 없는 업무 처리의 단위로 전체가 수행되거나 전혀 수행되지 않아야 함(All or Nothing)

```sql
START TRANSACTION;
state_ments;
...
[ROLLBACK|COMMIT];
```

- START TRANSACTION
  - 트랜잭션 구문의 시작을 알림
- COMMIT
  - 모든 작업이 정상적으로 완료되면 한꺼번에 DB에 반영
- ROLLBACK
  - 부분적으로 작업이 실패하면 트랜잭션에서 진행한 모든 연산을 취소하고 트랜잭션 실행 전으로 되돌림
- 기본적으로 MySQL은 자동으로 변경 사항을 COMMIT 함
- 변경 사항을 자동으로 COMMIT 하지 않으려면 'SET autocommit = 0;' 다음과 같이 설정

## 💡 트리거(Triggers)

- 특정 이벤트에 대한 응답으로 자동으로 실행되는 것

```sql
CREATE TRIGGER trigger_name
  {BEFORE|AFTER} {INSERT|UPDATE|DELETE}
  ON table_name FOR EACH ROW
  trigger_body;
```

- CREATE TRIGGER 키워드 다음에 생성하려는 트리거의 이름을 지정
- 각 레코드의 어느 시점에 트리커가 실행될지 지정(삽입, 수정, 삭제 전/후)
- ON 키워드 뒤에 트리거가 속한 테이블의 이름을 지정
- 트리거가 활성화될 때 실행할 코드를 trigger_body에 지정
  - 여러 명령문을 실행하려면 BEGIN END 키워드로 묶어서 사용

```sql
-- 트리거를 사용해 기존 게시글이 수정되면 게시글의 수정 일자 필드 값을 최신 일자로 업데이트하기
DELIMITER //
CREATE TRIGGER beforeArticleUpdate
  BEFORE UPDATE
  ON articles FOR EACH ROW
BEGIN
  SET NEW.updateAt = CURRENT_TIME();
END//
DELIMITER ;
```

- DELIMITER
  - SQL의 구문 문자(;)를 변경
  - BEGIN-END 구문 사이에 여러 SQL 문이 작성되기 때문에 하나의 트리거로써 작동될 수 있도록 사용
- BEGIN-END
  - 하나 이상의 구문 목록을 표현
  - BEGIN과 END 키워드로 둘러싸는 다중 구문을 구성하게 됨
- NEW

  - 트리거에서 특정 시점 전/후의 값에 접근할 수 있도록 제공하는 키워드
  - OLD와 NEW 2개 제공
  - 상황별 사용 여부  
    | |OLD|NEW|
    |---|-----|----|
    |INSERT|NO|YES|
    |UPDATE|YES|YES|
    |DELETE|YES|NO|

- Triggers 관련 추가 명령문
  - 트리거 목록 확인
  ```sql
  SHOW TRIGGERS;
  ```
  - 트리거 삭제
  ```sql
  DROP TRIGGER trigger_name;
  ```
- Triggers 생성 시 에러 해결

  - 트랜잭션 생성 후 정상적으로 종료되지 않아 에러가 발생할 시 해결법
  - Error Code:2013. Lost connection to MySQL server during query
  - Error Code: 2015. Lock wait timeout exceeded; try restarting transaction

  ```sql
  -- 실행 중인 프로세스 목록 확인
  SELECT * FROM information_schema.INNODB_TRX;

  -- 특정 프로세스의 trx_mysql_thread_id 삭제
  KILL [trx_mysql_thread_id1];
  ```

## 💡 정규화(Normalization)

- RDB 설계 단계에서 중복을 최소화하여 데이터를 구조화하는 과정
- 제1 정규화
  - 데이터베이스의 각 필드에는 하나의 값만 저장해야 함
  - 유사하게 정보를 저장하는 두 개의 필드가 있어서는 안 됨
    - 반복되는 부분을 찾아 테이블을 분할하고 기본 키가 될 필드를 작성
- 제2 정규화
  - 키값을 이용해 데이터를 특징지을 수 있는 것(함수 종속성)을 찾아 테이블을 분할
- 제3 정규화
  - 기본 키 이외의 부분에서 중복이 없는지를 조사하여 테이블을 분할
- 정규화의 목적
  - 데이터를 쉽게 관리하기 위해
    - 하나의 데이터를 무조건 한 곳에서만 위치하도록 함
    - 테이블 간의 관계는 키를 통해 형성
    - 데이터를 변경하더라도 한 곳만 변경하는 구조 확립

## 💡 데이터 모델링(Data Modeling)

- 데이터베이스 시스템을 시각적으로 표현하는 프로세스
- 데이터 유형, 데이터 간의 관계 및 분석 등을 통해 비즈니스 요구사항을 만들어 낼 수 있도록 도움
- ER(Entity-Relationship) Diagram
  - 다이어그램을 사용하여 데이터베이스의 Entity 간 관계를 나타내는 방법
  - Entity(□)는 사각형으로 나타내며 테이블을 나타냄
  - Attribute(○)는 원형으로 나타내며 필드를 나타냄
  - Relation(◇)은 마름모로 나타내며 관계(PK, FK)를 나타냄
  - Relationship 표현 방법
    - Cardinality(기수)
      - 1:1, 1:N, M:N 등 하나의 개체에 몇 개의 개체가 대응되는지 표현하는 것
    - Optionality(선택 가능성)
      - 관계가 필수인지 아닌지 표현하는 것
  - 데이터 모델링의 중요성
    - 데이터베이스 소프트웨어 개발 오류 감소
    - 데이터베이스 설계 및 생성 속도와 효율성 촉진
    - 조직 전체에서 데이터 문서화 및 시스템 설계의 일관성 조성
    - 데이터 엔지니어와 비즈니스팀 간의 커뮤니케이션 촉진
