# ⭐ (Python) 자릿수

## 💡 math 함수

- math 함수는 복소수와 함께 사용할 수 없음
- 따로 명시하지 않으면 모든 반환 값은 float임
- math.ceil(x): 올림
  - x보다 크거나 같은 가장 작은 정수인 x의 자릿수를 반환
- math.floor(x): 내림
  - x보다 작거나 같은 가장 큰 정수인 x의 자릿수를 반환
- math.trunc(x): 버림
  - 정수 부분을 남기고 나머지 부분을 제거한 상태에서 x를 반환

```python
import math

math.ceil(15.1)
# 16
math.ceil(15.7)
# 16

math.floor(15.1)
# 15
math.floor(15.7)
# 15

math.trunc(15.1)
# 15
math.trunc(15.7)
# 15
```

## 💡 round 함수

- round(number, ndigits=None)
- number를 소수점 다음에 ndigits 정밀도로 반올림한 값을 돌려줌
- ndigits가 생략되거나 None이면, 소수점 첫 번째 자리에서 반올림한 값을 돌려줌
- ndigits가 음수이면 정수 자리에 해당하는 곳에서 반올림한 값을 돌려줌

```python
n = 3/5
# 1.8571428571428572

round(n, 2)
# 1.86

round(n, 4)
# 1.8571

round(n)
# 2

round(12345, -1)
# 12340

round(12345, -2)
# 12300
```
