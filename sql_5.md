# ⭐ SQL Multi Table Queries

## 💡 Joining tables
- JOIN clause
  - 둘 이상의 테이블에서 데이터를 검색하는 방법
  - JOIN 종류
    - INNER JOIN
    - OUTER JOIN
      - LEFT JOIN
      - RIGHT JOIN

  - INNER JOIN clause
    - 두 테이블에서 값이 일치하는 레코드에 대해서만 결과를 반환
    ```sql
    SELECT
      select_list
    FROM
      table1
    INNER JOIN table2
      ON table1.fk = table2.pk;
    ```
    - FROM 절 이후 메인테이블 지정(table1)
    - INNER JOIN 절 이후 메인테이블과 조인할 테이블을 지정(table2)
    - ON 키워드 이후 조인 조건을 작성
      - 조인 조건은 table1과 table2 간의 레코드를 일치시키는 규칙을 지정
    ```sql
    -- 테이블 orders와 테이블 orderdetails를 INNER JOIN 하여 orderNumber 값이 같은 레코드의 orderNumber, status, priceEach 필드를 조회
    
    SELECT
      t1.orderNumber,
      t1.status,
      t2.priceEach
    FROM
      orders AS t1
    INNER JOIN orderdetails AS t2
      ON t1.orderNumber = t2.orderNumber;
    ```

  - LEFT [OUTER] JOIN clause
    - 오른쪽 테이블의 일치하는 레코드와 함께 왼쪽 테이블의 모든 레코드 반환
    ```sql
    SELECT
      select_list
    FROM
      table1
    LEFT [OUTER] JOIN table2
      ON table1.fk = table2.pk;
    ```
    - FROM 절 이후 왼쪽 테이블 지정(table1)
    - LEFT JOIN 절 이후 오른쪽 테이블 지정(table2)
    - ON 키워드 이후 조인 조건을 작성
      - 왼쪽 테이블의 각 레코드를 오른쪽 테이블의 모든 레코드와 일치시킴
    - 왼쪽은 무조건 표시하고, 매치되는 레코드가 없으면 NULL을 표시
    - 왼쪽 테이블 한 개의 레코드에 여러 개의 오른쪽 테이블 레코드가 일치할 경우 해당 왼쪽 레코드를 여러 번 표시
    ```sql
    -- customers 기준으로 customerNumber 필드가 일치하는 레코드와 함께 customers 테이블의 contactFirstName과 orders 테이블의 orderNumber, status 필드 조회(왼쪽 테이블은 customers, 오른쪽 테이블은 orders, 일치하지 않는 경우 NULL)

    SELECT
      contactFirstName,
      orderNumber,
      status
    FROM
      customers
    LEFT JOIN orders
      ON orders.customerNumber = customers.customerNumber;
    ```

  - RIGHT [OUTER] JOIN clause
    - 왼쪽 테이블의 일치하는 레코드와 함께 오른쪽 테이블의 모든 레코드 반환
    ```sql
    SELECT
      select_list
    FROM
      table1
    RIGHT [OUTER] JOIN table2
      ON table1.fk = table2.pk;
    ```
    - FROM 절 이후 왼쪽 테이블 지정(table1)
    - RIGHT JOIN 절 이후 오른쪽 테이블 지정(table2)
    - ON 키워드 이후 조인 조건을 작성
      - 오른쪽 테이블의 각 레코드를 왼쪽 테이블의 모든 레코드와 일치시킴
    - 오른쪽을 무조건 표시하고, 매치되는 레코드가 없으면 NULL을 표시
    - 오른쪽 테이블 한 개의 레코드에 여러 개의 왼쪽 테이블 레코드가 일치할 경우 해당 오른쪽 레코드를 여러 번 표시
    ```sql
    -- employeeNumber 필드와 salesRepEmployeeNumber 필드가 일치하는 레코드와 함께 employeeNumber, firstName, customerNumber, contactFirstName 필드 조회(왼쪽 테이블은 customers, 오른쪽 테이블은 employees, 일치하지 않는 경우 NULL)

    SELECT
      employeeNumber,
      firstName,
      customerNumber,
      ContactFirstName
    FROM
      customers
    RIGHT JOIN employees
      ON salesRepEmployeeNumber = employeeNumber;
    ```

  - FULL [OUTER] JOIN clause
    - INNER, LEFT, RIGHT JOIN 집합을 모두 출력하는 JOIN 방식
    - 두 개 이상의 테이블 간 출력할 수 있는 모든 데이터를 포함한 집합을 출력
    - MySQL에서는 FULL OUTER JOIN을 지원하지 않으므로 LEFT JOIN과 RIGHT JOIN을 UNION 하여 FULL OUTER JOIN을 사용할 수 있음
    ```sql
    SELECT * FROM tableA
    LEFT JOIN tableB ON tableA.fk = tableB.id
    UNION
    SELECT * FROM tableA
    RIGHT JOIN tableB ON tableB.fk = tableB.id;
    ```