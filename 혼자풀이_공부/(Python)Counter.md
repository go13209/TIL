# ⭐ (Python) Counter 클래스

- Counter는 해시 가능한 개체 수를 세는 딕셔너리 하위 클래스
- 요소가 딕셔너리 키로 저장되고 카운트가 값으로 저장되는 컬렉션
- Counter 클래스 자체는 키와 값에 제한이 없는 딕셔너리 서브 클래스로 값은 개수를 나타내는 숫자로 의도되었지만, 값 필드에 어떤 것이든 저장할 수 있음

```python
from collections import Counter

Counter(['red', 'blue', 'red', 'green', 'blue', 'blue'])
# Counter({'blue': 3, 'red': 2, 'green': 1})
```

- most_common([n])
  - n개의 가장 흔한 요소와 그 개수를 가장 흔한 것부터 가장 적은 것 순으로 나열한 리스트를 반환
  - n이 생략되거나 None이면, most_common()은 모든 요소를 반환하며 개수가 같은 요소는 처음 발견된 순서로 정렬됨

```python
Counter('abracadabra').most_common(3)
# [('a', 5), ('b', 2), ('r', 2)]
```

- Countersms 객체를 결합하여 다중 집합을 생성하기 위한 여러 수학적 연산이 가능함
- 카운트가 0 이하인 결과는 출력에서 제외됨

```python
c = Counter(a=3, b=1)
d = Counter(a=1, b=2)

c + d
# Counter({'a': 4, 'b': 3})

c - d
# Counter({'a': 2})

c & d
# Counter({'a': 1, 'b': 1})

c | d
# Counter({'a': 3, 'b': 2})

c == d
# False

c <= d
# False
```
