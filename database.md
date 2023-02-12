# 관계형 데이터베이스(Relational Database)

## 💡 관계형 데이터베이스란?

- 데이터 간에 **관계**가 있는 데이터 항목들의 모음
- 테이블, 행, 열의 정보를 구조화하는 방식
- 테이블을 조인하여 **정보 간 관계 또는 링크를 설정**할 수 있어 **여러 데이터 포인트 간의 관계**를 쉽게 이해하고 정보를 얻을 수 있음
- 모든 테이블에는 행에서 고유하게 식별 가능한 **기본 키**라는 속성이 있으며 **외래 키**를 사용하여 각 행에서 서로 다른 테이블 간의 관계를 만들 수 있음

## 💡 관계형 데이터베이스 용어 정리

- Table(= Relation)
  - 세로줄과 가로줄의 모델을 이용하여 정렬된 데이터 집합의 모임
  - 데이터를 기록하는 곳
- Field(= Column, Attribute)
  - 데이터의 이름이 되는 요소와 그에 해당하는 데이터 값들의 모임
  - 각 필드에는 고유한 데이터 형식(타입)이 지정됨
  - 예시: '이름', '주소'
- Record(= Row, Tuple)
  - 단일 구조 데이터 항목
  - 각 레코드에는 구체적인 데이터 값이 저장됨
  - 예시: '홍길동', '서울'
- Database(= Schema)
  - 테이블의 집합
- Primary Key(기본 키)
  - 각 레코드의 고유한 값
  - 관계형 데이터베이스에서 레코드의 식별자로 활용
- Foreign Key(외래 키)
  - 테이블의 필드 중 다른 테이블의 레코드를 식별할 수 있는 키
  - 각 레코드에서 서로 다른 테이블 간의 관계를 만드는 데 사용

## 💡 RDBMS(Relational Database Management System)

- 관계형 데이터베이스를 관리하는 소프트웨어 프로그램
- 데이터 저장 및 관리를 용이하게 하는 시스템
- 데이터베이스와 사용자 간의 인터페이스 역할
- 대표적인 RDBMS
  - MySQL
  - PostgreSQL
  - Oracle Database
  - MS SQL Server

## 💡 MySQL

- 가장 널리 사용되는 오픈 소스 RDBMS
- 다양한 운영체제에서 실행가능
- 여러 프로그래밍 언어를 위한 다양한 API 제공
- MySQL Workbench Tool을 통해 그래픽 인터페이스(GUI)를 제공

## 💡 Workbench 활용 MySQL 접속 방법

1. MySQL 사이트에서 버전을 선택하고 클라이언트를 다운받아 설치
2. MySQL Server와 MySQL Workbench가 설치된 것을 확인
3. 설치된 Workbench를 열면 MySQL Connections 하단에 root 사용자가 있는 걸 확인
4. MySQL을 설치하면 가장 처음에 root라는 사용자가 기본으로 준비되어 있으며 설치 설정 중 입력했던 비밀번호를 입력하여 서버에 접속

## 💡 쿼리(Query)문 작성 및 쿼리문 실행 방법

1. MySQL에 접속하여 'Date Import/Restore'를 클릭
2. 'Import from Self-Contained File'을 체크한 뒤 불러올 sql 파일을 선택하고 'Start Import' 버튼을 클릭
3. 'Import Completed' 문구를 확인한 뒤 왼편 하단의 'Schemas'를 클릭
4. 'SCHEMAS' 오른쪽의 새로고침을 눌러 import된 데이터베이스를 확인
5. 원하는 데이터베이스를 더블 클릭하고 Query 에디터를 클릭하여 쿼리문을 입력
6. 쿼리문을 입력한 뒤 번개 모양의 쿼리 실행 버튼을 클릭하면 쿼리에 따른 내용 출력

## 💡 한글 입력 설정

> MySQL은 기본적으로 한글 데이터 입력이 불가능하므로 추가 설정이 필요

1.  데이터베이스 옆 렌치 모양의 도구 설정을 클릭
2.  'utf8'과 'utf8_bin'으로 변경하고 'Apply' 버튼을 클릭하면 한글 입력이 가능