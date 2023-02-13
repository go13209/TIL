# ⭐ (SQL) 문자열 추출 방법

## 💡 substring

- SUBSTRING(string, start, length)
- 문자열의 `start` 위치부터 지정된 개수의 문자를 읽음
- 파이썬 인덱스와는 달리 1부터 시작하며 (length - 1)이 아닌 지정된 길이만큼의 문자를 읽음

```sql
SELECT
  SUBSTRING(country, 1, 3)
FROM
  orders
WHERE store_name = 'Korea';

-- 결과: Kor
```
