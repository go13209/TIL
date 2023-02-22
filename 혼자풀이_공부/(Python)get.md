# ⭐ (Python) get 메소드

- 딕셔너리의 메소드
- get(key[, default])
- key가 딕셔너리에 있는 경우 key에 대응하는 값을 돌려주고, 그렇지 않으면 default를 돌려줌
- default 가 주어지지 않으면 기본값 None이 사용되므로 이 메소드는 절대로 KeyError를 일으키지 않음

```python
d = {"one": 1, "two": 2, "three": 3, "four": 4}

d.get("one")
# 1

d.get("five")
# None

d.get("five", 0)
# 0
```
