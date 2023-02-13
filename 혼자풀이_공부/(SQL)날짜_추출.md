# ⭐ (SQL) 날짜 추출 방법

## 💡 extract

- EXTRACT(part FROM date)
- 특정 날짜/시간 값을 가진 표현식으로부터 원하는 날짜 영역을 추출하여 읽음
- `part` 부분에 올 수 있는 값
  - year: 연도
  - month: 월
  - day: 일
  - hour: 시
  - minute: 분
  - second: 초

```sql
SELECT EXTRACT(MINUTE FROM "2017-06-15 09:34:21");

-- 결과: 34

SELECT EXTRACT(YEAR_MONTH FROM "2017-06-15 09:34:21");

-- 결과: 201706
```

## 💡 year, month, day

- year|month|day(date)
- 날짜 데이터의 년, 월, 일을 추출할 때 사용하는 함수
- 정수로 결과를 반환함

```sql
SELECT YEAR('1998/05/25 09:08') AS Year;

-- 결과: 1998
```
