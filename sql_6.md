# ⭐ SQL Nested Queries

## 💡 Subquery
- 단일 쿼리문에 여러 테이블의 데이터를 결합하는 방법
- 조건에 따라 하나 이상의 테이블에서 데이터를 검색하는 데 사용
- SELECT, FROM, WHERE, HAVING 절 등에서 다양한 맥락에서 사용
```sql
-- 소비를 한 고객 중 한 번에 지불한 금액이 가장 높은 고객의 customerNumber, amount, contactFirstName을 조회(고객 테이블은 customers, 지불 테이블은 payments를 활용)

SELECT customerNumber, amount, contactFirstName
FROM (
	SELECT *
    FROM payments
    INNER JOIN customers USING (customerNumber)
) AS mySub
WHERE amount = (
	SELECT MAX(amount)
    FROM payments
);
```
- EXISTS operator
  - 쿼리문에서 반환된 레코드의 존재 여부를 확인
  ```sql
  SELECT
    select_list
  FROM
    table
  WHERE
    [NOT] EXISTS (subquery);
  ```
  - subquery가 하나 이상의 행을 반환하면 EXISTS 연산자는 true를 반환하고 그렇지 않으면 false를 반환
  - 주로 WHERE 절에서 subquery의 반환 값 존재 여부를 확인하는 데 사용
  ```sql
  -- Paris에 있는 사무실에서 일하는 모든 직원의 번호, 이름, 성을 조회(직원 테이블은 employees, 사무실 테이블은 offices이며 두 테이블의 officeCode 필드를 기준으로 비교)

  SELECT
    employeeNumber, firstName, lastName
  FROM
    employees
  WHERE
    EXISTS (
      SELECT *
      FROM offices
      WHERE city = 'Paris' AND offices.officeCode = employees.officeCode
    );
  ```

  ## 💡 CASE statement
  - SQL 문에서 조건문을 구성
  ```sql
  CASE case_value
    WHEN when_value1 THEN statements
    WHEN when_value2 THEN statements
    ...
    [ELSE else-statements]
  END CASE;
  ```
  - case_value가 when_value와 동일한 것을 찾을 때까지 순차적으로 비교
  - when_value와 동일한 case_value를 찾으면 해당 THEN 절의 코드를 실행
  - 동일한 값을 찾지 못하면 ELSE 절의 코드를 실행
    - ELSE 절이 없을 때 동일한 값을 찾지 못하면 오류 발생
  ```sql
  -- orders 테이블의 status에 따라 상세 정보를 매겨 조회('In Process'는 '주문중', 'Shipped'는 '발주완료', 'Cancelled'는 '주문취소', 그 외는 '기타사유'로 지정)

  SELECT orderNumber, status,
    CASE
      WHEN status = 'In Process' THEN '주문중'
      WHEN status = 'Shipped' THEN '발주완료'
      WHEN status = 'Cancelled' THEN '주문취소'
      ELSE '기타사유'
    END AS details
  FROM orders;
  ```