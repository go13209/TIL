# ⭐ SQL Managing Tables

## 💡 CREATE TABLE statement 
- 테이블 생성
```sql
CREATE TABLE table_name (
  column_1 data_type,
  column_2 data_type,
  ...,
  constraints
);
```
- 각 필드에 적용할 데이터 타입(data type) 작성
- 테이블 및 필드에 대한 제약 조건(constraints) 작성
  > 제약 조건(Constraint): `데이터 무결성`을 지키기 위해 데이터를 입력받을 때 실행하는 검사 규칙  
  
  > 데이터 무결성: 데이터의 정확성과 일관성을 보증
  - PRIMARY KEY: 해당 필드를 기본 키로 지정
  - NOT NULL: 해당 필드에 NULL 값을 저장하지 못하도록 지정
    - 반드시 NOT NULL 제약을 사용할 필요는 없으나 데이터베이스를 사용하는 프로그램에 따라 NULL을 저장할 필요가 없는 경우가 많으므로 되도록 NOT NULL로 정의
    - '값이 없다'라는 표현을 테이블에 기록하는 것은 0이나 빈 문자열 등을 사용하는 것으로 대체하는 것을 권장

- AUTO_INCREMENT attribute
  - 테이블의 기본 키에 대한 번호 자동 생성
  - 기본 키 필드에 사용
    - 고유한 숫자를 부여
  - 시작 값은 1이며 데이터 입력 시 값을 생략하면 자동으로 1씩 증가
  - 이미 사용한 값을 재사용하지 않음
  - 기본적으로 NOT NULL 제약 조건을 포함

```sql
CREATE TABLE examples (
  examId INT AUTO_INCREMENT,
  lastName VARCHAR(50) NOT NULL,
  firstName VARCHAR(50) NOT NULL,
  PRIMARY KEY (examId)
);
```

## 💡 DROP TABLE statement
- 테이블 삭제
```sql
DROP TABLE table_name;
```
- DROP TABLE statement 이후 삭제할 테이블 이름 작성

## 💡 ALTER TABLE statement
- 테이블 필드 조작(생성, 수정, 삭제)
- ALTER TABLE **ADD** : 필드 추가
  ```sql
  ALTER TABLE
    table_name
  ADD
    new_column_name column_definition;
  ```
  - ADD 이후 추가하고자 하는 새 필드 이름과 데이터 타입 및 제약 조건 작성
  ```sql
  -- examples 테이블에 country 필드 추가(단, country 필드는 가변 길이 문자열 최대 100자이며 NULL  값을 허용하지 않음)

  ALTER TABLE
    examples
  ADD
    country VARCHAR(100) NOT NULL;
  ```
- ALTER TABLE **MODIFY** : 필드 속성 변경
  ```sql
  ALTER TABLE
    table_name
  MODIFY
    column_name column_definition;
  ```
  - MODIFY 키워드 이후 변경하고자 하는 필드 이름, 데이터 타입 및 제약 조건 작성
  ```sql
  -- examples 테이블의 lastName, firstName 필드를 가변 길이 문자열 최대 10자까지 그리고 NULL 값을 허용하지 않도록 변경

  ALTER TABLE examples
  MODIFY lastName VARCHAR(10) NOT NULL,
  MODIFY firstName VARCHAR(10) NOT NULL;
  ```

- ALTER TABLE **CHANGE COLUMN** : 필드 이름 변경
  ```sql
  ALTER TABLE
    table_name
  CHANGE COLUMN
    original_name new_name column_definition;
  ```
  - CHANGE COLUMN 키워드 이후 기존 필드 이름, 변경하고자 하는 필드 이름, 데이터 타입 및 제약 조건 작성
  ```sql
  -- examples 테이블의 country 필드 이름을 state로 변경(단, 데이터 타입 및 제약 조건은 기존과 동일)
  
  ALTER TABLE
    examples
  CHANGE COLUMN
    country state VARCHAR(100) NOT NULL;
  ```

- ALTER TABLE **DROP COLUMN** : 필드 삭제
  ```sql
  ALTER TABLE
    table_name
  DROP COLUMN
    column_name;
  ```
  - DROP COLUMN 키워드 이후 삭제하고자 하는 필드 이름 작성
  ```sql
  -- examples 테이블의 state와 age 필드 삭제

  ALTER TABLE
    examplese
  DROP COLUMN
    state,
  DROP COLUMN
    age;
  ```