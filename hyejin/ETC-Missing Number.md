## 2023-05-03 / 김혜진 / LeetCode-Missing Number

```python
class Solution:
    def missingNumber(self, nums: List[int]) -> int:
        return len(nums)*(len(nums)+1)//2 - sum(nums)
```

- 시간복잡도/공간복잡도: O(n)
- O(n)으로 푸는 많은 방법이 있겠지만 수학적으로 접근해서 런타임을 많이 줄일 수 있었다.
