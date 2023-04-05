## 2023-04-05 / 이근탁 / PGS-위장

```python
def solution(clothes):
    answer = 1
    closet = {}
    for tp in clothes:
        if tp[1] not in closet:
            closet[tp[1]] = 1
        else:
            closet[tp[1]] += 1
    for tp in closet:
        answer *= closet[tp] + 1

    return answer - 1
```

- 시간복잡도/공간복잡도: O(n)/O(n)
