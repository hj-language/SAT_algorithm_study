## 2023-04-13 / 박준수 / PGS-삼각 달팽이


```python
def solution(n):
    answer = []
    
    snail = [[0]*n for _ in range(n)]
    
    number = 1
    x, y = -1, 0
    
    for i in range(n):
        for j in range(i, n):
            if i % 3 == 0:
                x += 1
            
            if i% 3 == 1:
                y += 1
            
            if i % 3 == 2:
                x -= 1
                y -= 1
            
            snail[x][y] = number
            number += 1
            
    for i in snail:
        for j in i:
            if(j != 0):
                answer.append(j)
            
    return answer

```

-   시간복잡도/공간복잡도: O(n^2)/O(n)
