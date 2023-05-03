# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
0의 위치를 저장해두고 해당 row, col 을 for로 돌면서 0으로 바꾼다.

# Approach
<!-- Describe your approach to solving the problem. -->
Intuition과 동일

# Complexity
- Time complexity: O(n\*m\*k) - n: 가로, m: 세로, k: 0의 개수
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(n*m)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```python
class Solution:
    def setZeroes(self, matrix: List[List[int]]) -> None:
        """
        Do not return anything, modify matrix in-place instead.
        """
        zeros = []
        for i in range(len(matrix)):
            for j in range(len(matrix[i])):
                if matrix[i][j] == 0:
                    zeros.append((i, j))
        for i, j in zeros:
            for k in range(len(matrix)): matrix[k][j] = 0
            for k in range(len(matrix[i])): matrix[i][k] = 0
```
