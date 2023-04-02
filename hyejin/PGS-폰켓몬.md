### 2023-04-02 / 김혜진 / PGS-폰켓몬

- 언어: Python3
```python
    def solution(nums):
        s = len(set(nums))
        max = len(nums) // 2
        return s if s < max else max
```

- 시간복잡도/공간복잡도: O(n)/O(n)
- 총 개수가 아니라 종류 수를 구하는 문제라 set만 떠올리면 어렵지 않게 풀 수 있었다.
