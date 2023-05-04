## 2023-05-04 / 이근탁 / Missing Number

```python
class Solution:
    def missingNumber(self, nums: List[int]) -> int:
        nums = sorted(nums)
        for idx, value in enumerate(nums):
            if idx != nums[idx]:
                return idx
        else:
            return len(nums)
```

- 시간복잡도/공간복잡도: O(n)
- EZ
