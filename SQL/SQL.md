# SQL

- SQL(Structure Query Language)이란?
    - 테이블의 형태로 **구조화**된 관계형 데이터베이스에 요청을 **질의(요청)**하기 위한 프로그래밍 언어
    - 데이터베이스에 정보를 저장하고 처리하기 위한 프로그래밍 언어
    - SQL은 미국 국립 표준 협회(ANSI)와 국제 표준화 기구(ISO)에 의해 표준이 채택됨
    - 널리 사용되는 모든 RDBMS에서 SQL 표준을 지원
    - 단, **RDBMS별로 독자적인 기능에 따라 표준을 벗어나는 문법이 존재할 수 있음**
    
- SQL Statements
    - SQL 언어를 구성하는 가장 기본적인 코드 블록
    
    ```sql
    SELECT column_name FROM table_name;
    ```
    
    - 위의 예시 코드는 SELECT Statement라고 부르며, 해당 Statement는 SELECT, FROM 2개의 Keyword로 구성됨
    - SQL 키워드는 대소문자를 구분하지 않으나 명시적 구분을 위해 대문자로 작성하는 것을 권장함
    - 각 SQL Statements의 끝에는 세미콜론(;)이 필요하여 세미콜론이 각 SQL Statemets를 구분하는 역할을 함
    - SQL Statements 유형(수행 목적에 따른 분류)
        - DDL(Data Definition Language)
            - 데이터 정의
            - 데이터의 기본 구조 및 형식 변경
            - CREATE, DROP, ALTER
        - DQL(Data Query Language)
            - 데이터 검색
            - SELECT
        - DML(Data Manipulate Language)
            - 데이터 조작(추가, 수정, 삭제)
            - INSERT, UPDATE, DELETE
        - DCL(Data Control Language)
            - 데이터 제어
            - 데이터 및 작업에 대한 사용자 권한 제어
            - COMMIT, ROLLBACK, GRANT, REVOKE
            
- SQL Single Table Queries
    - Querying data
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
            
            - *(Asterisk): 모든 데이터 조회 가능
            - AS keyword: 필드에 새로운 별칭을 지정
            - 기본적인 사칙연산 사용 가능
    - Sorting data
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
                
    - Filtering data
        - DISTINCT clause
            - 조회 결과에서 중복된 레코드를 제거
            
            ```sql
            SELECT DISTINCT
            	select_list
            FROM
            	table_name;
            ```
            
            - SELECT 키워드 바로 뒤에 작성해야 함
            - SELECT DISTINCT 키워드 다음에 고유한 값을 선택하려는 하나 이상의 지정
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
            - search_condition은 비교 연산자(=, >=, <=, IS, LIKE, IN, BETWEEN 등) 및 논리 연산자(AND(&&), OR(||), NOT(!) 등)를 사용하는 구문이 사용됨
            - 특정 범위를 지정할 때는 BETWEEN 연산자 사용 가능
                
                ```sql
                -- 테이블 employees에서 officeCode 필드 값이 1에서 4 사잇값인 데이터의 lastName, firstName, officeCode 조회(1과 4 포함)
                
                SELECT
                	lastName, firstName, officeCode
                FROM
                	employees
                WHERE
                	officeCode >= 1  AND officeCode <= 4;
                
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
                    - ‘%’ : **0개 이상의 문자열**과 일치하는지 확인
                    - ‘_’ : **단일 문자**와 일치하는지 확인
                
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
            
    - Grouping data
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
            
- SQL Managing Tables
    - CREATE TABLE statement
        - 테이블 생성
        
        ```sql
        CREATE TABLE table_name (
          column_1 data_type,
          column_2 data_type,
          ...,
          constraints);
        ```
        
        - 각 필드에 적용할 데이터 타입(data type) 작성
        - 테이블 및 필드에 대한 제약 조건(constraints) 작성
            
            > 제약 조건(Constraint): `데이터 무결성`을 지키기 위해 데이터를 입력 받을 때 실행하는 검사 규칙
            > 
            
            > 데이터 무결성: 데이터의 정확성과 일관성을 보증
            > 
            - PRIMARY KEY: 해당 필드를 기본 키로 지정
            - NOT NULL: 해당 필드에 NULL 값을 저장하지 못하도록 지정
                - 반드시 NOT NULL 제약을 사용할 필요는 없으나 데이터베이스를 사용하는 프로그램에 따라 NULL을 저장할 필요가 없는 경우가 많으므로 되도록 NOT NULL로 정의
                - ’값이 없다’라는 표현을 테이블에 기록하는 것은 0이나 빈 문자열 등을 사용하는 것으로 대체하는 것을 권장
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
        
    - DROP TABLE statement
        - 테이블 삭제
        
        ```sql
        DROP TABLE table_name;
        ```
        
        - DROP TABLE statement 이후 삭제할 테이블 이름 작성
    - ALTER TABLE statement
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
            -- examples 테이블에 country 필드 추가(단, country 필드는 가변 길이 문자열 최대 100자이며 NULL 값을 허용하지 않음)
            
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
            	table_name
            DROP COLUMN
            	state,
            DROP COLUMN
            	age;
            ```
            
- SQL Modifying Data
    - INSERT statement
        - 테이블 레코드 삽입
        
        ```sql
        INSERT INTO table_name (c1, c2, ...)
        VALUES (v1, v2, ...);
        ```
        
        - INSERT INTO 절 다음에 테이블 이름과 괄호 안에 필드 목록을 작성
        - VALUES 키워드 다음 괄호 안에 해당 필드에 삽입할 값 목록을 작성
        
        ```sql
        -- articles 테이블에 각 필드에 적합한 데이터 입력(단, createdAt 필드에는 현재 작성하는 날짜가 자동으로 입력, 나머지 필드 자율)
        
        INSERT INTO
        	articles (title, content, createdAt)
        VALUES
        	('mytitle', 'mycontent', CURDATE());
        ```
        
        - `CURDATE()`: MySQL이 제공하는 Date Functions 중 하나로 현재 날짜를 반환함
    - UPDATE statement
        - 테이블 레코드 수정
        
        ```sql
        UPDATE table_name
        SET column_name = expression,
        [WHERE
        	condition];
        ```
        
        - SET 절 다음에 수정할 필드와 새 값을 지정
        - WHERE 절에서 수정할 레코드를 지정하는 조건 작성
            - WHERE 절을 작성하지 않으면 모든 레코드를 수정함
        - REPLACE(필드명, '기존 문자열', '변경 문자열') : MySQL이 제공하는 String Functions 중 하나로 지정된 문자열을 변경함
        
        ```sql
        -- articles 테이블 모든 레코드의 content 필드 값 중 문자열 'content'를 'TEST'로 변경
        
        UPDATE
        	articles
        SET
        	content = REPLACE(content, ‘content’, ‘TEST’);
        ```
        
    - DELETE statement
        - 테이블 레코드 삭제
        
        ```sql
        DELETE FROM table_name
        [WHERE
        	condition];
        ```
        
        - DELETE FROM 절 다음에 테이블 이름 작성
        - WHERE 절에서 삭제할 레코드를 지정하는 조건 작성
            - WHERE 절을 작성하지 않으면 모든 레코드를 삭제함
        
        ```sql
        -- articles 테이블의 1번 레코드 삭제
        
        DELETE FROM
        	articles
        WHERE
        	id = 1;
        ```
        
        ```sql
        -- articles 테이블에서 가장 최근에 작성된 레코드 2개를 삭제
        
        DELETE FROM
          articles
        ORDER BY
          createdAt DESC
        LIMIT 2;
        ```
        
- SQL Multi Table Queries
    - Joining tables
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
                
                - FROM 절 이후 메인 테이블 지정(table1)
                - INNER JOIN 절 이후 메인 테이블과 조인할 테이블을 지정(table2)
                - ON 키워드 이후 조인 조건을 작성
                    - 조인 조건은 table1과 table2 간의 레코드를 일치시키는 규칙을 지정
                
                ```sql
                -- 테이블 orders와 테이블 orderdetails를 INNER JOIN 하여 orderNumber 값이 같은 레코드의 orderNumber, status, priceEach 필드를 조회
                
                SELECT
                	t1.orderNumber,
                	t1.status,
                	t2.priceEach
                FROM orders AS t1
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
                
- SQL Nested Queries
    - Subquery
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
            
    - CASE statement
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
        -- orders 테이블의 status에 따라 상세 정보를 매겨 조회(‘In Process’는 ’주문중’, ‘Shipped’는 ’발주완료’, ‘Cancelled’는 ’주문취소’, 그 외는 ’기타사유’로 지정)
        
        SELECT orderNumber, status,
        	CASE
        		WHEN status = 'In Process' THEN '주문중'
        		WHEN status = 'Shipped' THEN '발주완료'
        		WHEN status = 'Cancelled' THEN '주문취소'
        		ELSE '기타사유'
        	END AS details
        FROM orders;
        ```
        
- SQL 심화
    - 트랜잭션(Transactions)
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
        - 변경 사항을 자동으로 COMMIT 하지 않으려면 ‘SET autocommit = 0;’ 다음과 같이 설정
    - 트리거(Triggers)
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
                
                
                |  | OLD | NEW |
                | --- | --- | --- |
                | INSERT | NO | YES |
                | UPDATE | YES | YES |
                | DELETE | YES | NO |
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
            
    - 정규화(Normalization)
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
    - 데이터 모델링(Data Modeling)
        - 데이터베이스 시스템을 시각적으로 표현하는 프로세스
        - 데이터 유형, 데이터 간의 관계 및 분석 등을 통해 비즈니스 요구 사항을 만들어 낼 수 있도록 도움
        - ER(Entity-Relationship) Diagram
            - 다이어그램을 사용하여 데이터베이스의 Entity 간 관계를 나타내는 방법
            - Entity(□)는 사각형으로 나타내며 테이블을 나타냄
            - Attribute(○)는 원형으로 나타내며 필드를 나타냄
            - Relation(◇)은 마름모로 나타내며 관계(PK, FK)를 나타냄
            - Relationship 표현 방법
                - Cardinality (기수)
                    - 1:1, 1:N, M:N 등 하나의 개체에 몇 개의 개체가 대응되는지 표현하는 것
                - Optionality (선택 가능성)
                    - 관계가 필수인지 아닌지 표현하는 것
            - 데이터 모델링의 중요성
                - 데이터베이스 소프트웨어 개발 오류 감소
                - 데이터베이스 설계 및 생성 속도와 효율성 촉진
                - 조직 전체에서 데이터 문서화 및 시스템 설계의 일관성 조성
                - 데이터 엔지니어와 비즈니스 팀 간의 커뮤니케이션 촉진