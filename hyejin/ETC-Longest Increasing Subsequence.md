# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
2중으로 반복하면서 피봇보다 크면 수열의 길이를 1씩 늘린다.

# Approach
<!-- Describe your approach to solving the problem. -->
1씩 늘린 결과와 그 전 결과 중 더 큰 값을 결과로 취한다. (Greedy 중 하나로 봐야 하나 ..)
최종으로 가장 큰 값이 정답이다.

# Complexity
- Time complexity: O(n^2)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution:
    def lengthOfLIS(self, nums: List[int]) -> int:
        sol = [1]*len(nums)
        for i in range(len(nums)):
            for j in range(i+1, len(nums)):
                if nums[i] < nums[j]:
                    sol[j] = max(sol[j], sol[i]+1)
        return max(sol)
```
