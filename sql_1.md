# ⭐ SQL(Structure Query Language)

## 💡 SQL(Structure Query Language)이란?

- 테이블의 형태로 **구조화**된 관계형 데이터베이스에 요청을 **질의(요청)**하기 위한 프로그래밍 언어
- 데이터베이스에 정보를 저장하고 처리하기 위한 프로그래밍 언어
- SQL은 미국 국립 표준 협회(ANSI)와 국제 표준화 기구(ISO)에 의해 표준이 채택됨
- 널리 사용되는 모든 RDBMS에서 SQL 표준을 지원
- 단, **RDBMS별로 독자적인 기능에 따라 표준을 벗어나는 문법이 존재할 수 있음**

## 💡 SQL Statements

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
