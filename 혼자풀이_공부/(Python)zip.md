# ⭐ (Python) zip 함수

- 여러 반복 가능한 항목을 병렬로 반복하여 각 항목에서 튜플을 생성하는 함수
- 요소는 for 루프 또는 목록으로 래핑하는 등 반복될 때까지 처리되지 않음

```python
for item in zip([1, 2, 3], ['sugar', 'spice', 'everything nice']):
  print(item)

# (1, 'sugar')
# (2, 'spice')
# (3, 'everything nice')
```

- zip()으로 전달된 반복 가능한 객체의 길이는 서로 다를 수 있음

- 기본적으로 zip()은 가장 짧은 길이의 객체 값이 모두 사용될 때 중지되며 더 긴 객체의 나머지 항목을 무시하고 결과를 가장 짧은 길이로 잘라냄

```python
list(zip(range(3), ['fee', 'fi', 'fo', 'fum']))
# [(0, 'fee'), (1, 'fi'), (2, 'fo')]
```

- 연산자와 함께 zip()을 쓰면 리스트를 unzip 할 수 있음

```python
x = [1, 2, 3]
y = [4, 5, 6]

list(zip(x, y))
# [(1, 4), (2, 5), (3, 6)]

x2, y2 = zip(*zip(x, y))
x == list(x2) and y == list(y2)
# True
```

- zip()을 활용하여 리스트나 튜플을 사전으로 변환할 수 있음

```python
keys = ['a', 'b', 'c']
values = [1, 2, 3]
dict(zip(keys, values))
# {'a': 1, 'b': 2, 'c': 3}
```
