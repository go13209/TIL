# ⭐ SQL Single Table Queries

## 💡 Querying data
- SELECT syntax
  - 테이블에서 데이터를 조회
  - SELECT 키워드 다음에 데이터를 선택하려는 필드를 하나 이상 지정
  - FROM 키워드 다음에 데이터를 선택하려는 테이블의 이름을 지정
  ```sql
  SELECT
    select_list
  FROM
    table_name;
  ```
  - \*(Asterisk): 모든 데이터 조회 가능
  - AS keyword: 필드에 새로운 별칭을 지정
  - 기본적인 사칙연산 사용 가능

## 💡 Sorting data
- ORDER BY clause
  - 조회 결과의 레코드를 정렬
  - FROM clause 뒤에 위치
  - 하나 이상의 필드를 기준으로 결과를 오름차순, 내림차순으로 정렬할 수 있음
    - ASC: 오름차순(기본값)
    - DESC: 내림차순
  ```sql
  SELECT
    select_list
  FROM
    table_name
  ORDER BY
    column1 [ASC|DESC],
    column2 [ASC|DESC],
    ...;
  ```

## 💡 Filtering data
- DISTINCT clause
  - 조회 결과에서 중복된 레코드를 제거
  ```sql
  SELECT DISTINCT
    select_list
  FROM
    table_name;
  ```
  - SELECT 키워드 바로 뒤에 작성해야 함
  - SELECT DISTINCT 키워드 다음에 고유한 값을 선택하려는 하나 이상의 필드를 지정

- WHERE clause
  - 조회 시 특정 검색 조건을 지정
  ```sql
  SELECT
    select_list
  FROM
    table_name
  WHERE
    search_condition;
  ```

  - FROM clause 뒤에 위치
  - search_condition은 비교연산자(=, >=, <=, IS, LIKE, IN, BETWEEN 등) 및 논리연산자(AND(&&), OR(||), NOT(!) 등)를 사용하는 구문이 사용됨
  - 특정 범위를 지정할 때는 BETWEEN 연산자 사용 가능

    ```sql
    -- 테이블 employees에서 officeCode 필드 값이 1에서 4 사잇값인 데이터의 lastName, firstName, officeCode 조회(1과 4 포함)

    SELECT
      lastName, firstName, officeCode
    FROM
      employees
    WHERE
      officeCode >= 1
      AND officeCode <= 4;


    SELECT
      lastName, firstName, officeCode
    FROM
      employees
    WHERE
      officeCode BETWEEN 1 AND 4;

    -- 두 쿼리문 모두 동일한 데이터를 조회함
    ```

  - IN operator

    - 값이 특정 목록 안에 있는지 확인

    ```sql
    -- 테이블 employees에서 officeCode 필드 값이 1 또는 3 또는 4 값인 데이터의 lastName, firstName, officeCode 조회

    SELECT
      lastName, firstName, officeCode
    FROM
      employees
    WHERE
      officeCode = 1
      OR officeCode = 3
      OR officeCode = 4;


    SELECT
      lastName, firstName, officeCode
    FROM
      employees
    WHERE
      officeCode IN (1, 3, 4);

    -- 두 쿼리문 모두 동일한 데이터를 조회함
    ```

  - LIKE operator

    - 와일드카드로 값이 특정 패턴과 일치하는지 확인
    - Wildcard characters
      - '%' : **0개 이상의 문자열**과 일치하는지 확인
      - '\_' : **단일 문자**와 일치하는지 확인

    ```sql
    -- 테이블 employees에서 lastName 필드 값이 'son'으로 끝나는 데이터의 lastName, firstName 조회

    SELECT
      lastName, firstName
    FROM
      employees
    WHERE
      lastName LIKE '%son';
    ```

    ```sql
    -- 테이블 employees에서 firstName 필드 값이 4자리이면서 'y'로 끝나는 데이터의 lastName, firstName 조회

    SELECT
      lastName, firstName
    FROM
      employees
    WHERE
      firstName LIKE '___y';
    ```

- LIMIT clause

  - 조회하는 레코드 수를 제한

  ```sql
  SELECT
    select_list
  FROM
    table_name
  LIMIT [offset,] row_count;
  ```

  - LIMIT clause는 하나 또는 두 개의 인자를 사용(0 또는 양의 정수)
  - row_count는 조회할 최대 레코드 수를 지정
  - offset 지정 수 이후부터 조회

  ```sql
  -- 테이블 customers에서 contactFirstName, creditLimit 필드 데이터를 creditLimit 기준 내림차순으로 4번째부터 7번째 데이터만 조회

  SELECT
    contactFirstName, creditLimit
  FROM
    customers
  ORDER BY
    creditLimit DESC
  LIMIT 3, 4;
  ```

## 💡 Grouping data
- GROUP BY clause
  - 집계 함수로 레코드를 그룹화하여 요약본 생성
  - 집계 함수(Aggregation Functions): 값에 대한 계산을 수행하고 단일한 값을 반환하는 함수
    - SUM, AVG, MAX, MIN, COUNT
  ```sql
  SELECT
    c1, c2, ..., cn, aggregate_function(ci)
  FROM
    table_name
  GROUP BY
    c1, c2, ..., cn;
  ```
  - FROM 및 WHERE 절 뒤에 배치
  - GROUP BY 절 뒤에 그룹화할 필드 목록을 작성
- HAVING clause
  - 집계 항목에 대한 세부 조건을 지정
  - 주로 GROUP BY와 함께 사용되며 GROUP BY가 없다면 WHERE처럼 동작
  ```sql
  -- 테이블 customers에서 country 필드를 그룹화하여 각 그룹에 대한 creditLimit의 평균값이 80,000을 초과하는 데이터만 조회

  SELECT
    country,
    AVG(CreditLimit)
  FROM
    customers
  GROUP BY
    country
  HAVING
    AVG(CreditLimit) > 80000;
  ```
