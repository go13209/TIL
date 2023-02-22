# ⭐ (Python) enumerate 함수

- enumerate(iterable, start=0)
- 열거 객체를 돌려주는 함수
- iterable은 시퀀스, 이터레이터 또는 이터레이션을 지원하는 다른 객체여야 하며 카운트(기본값 0을 갖는 start부터)와 iterable을 이터레이션해서 얻어지는 값을 포함하는 튜플을 돌려줌

```python
seasons = ['Spring', 'Summer', 'Fall', 'Winter']

list(enumerate(seasons))
# [(0, 'Spring'), (1, 'Summer'), (2, 'Fall'), (3, 'Winter')]

list(enumerate(seasons, start=1))
# [(1, 'Spring'), (2, 'Summer'), (3, 'Fall'), (4, 'Winter')]
```

- 다음과 동등한 결과

```python
def enumerate(iterable, start=0):
  n = start
  for elem in iterable:
    yield n, elem
    n += 1
```
