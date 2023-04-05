## 2023-04-05 / 이근탁 / PGS-폰켓몬

```python
def solution(nums):
    testSet = set(nums)
    if len(testSet) >= len(nums) // 2:
        return len(nums) // 2
    else:
        return len(testSet)
    answer = 0
    return answer
```

- 시간복잡도/공간복잡도: O(n)/O(n)
