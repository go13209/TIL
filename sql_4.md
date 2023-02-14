# ⭐ SQL Modifying Data

## 💡 INSERT statement
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

## 💡 UPDATE statement
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
```sql
-- articles 테이블 모든 레코드의 content 필드 값 중 문자열 'content'를 'TEST'로 변경

UPDATE
  articles
SET
  content = REPLACE(content, 'content', 'TEST');
```
- `REPLACE(필드명, '기존 문자열', '변경 문자열')` : MySQL이 제공하는 String Functions 중 하나로 지정된 문자열을 변경함

## 💡 DELETE statement
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