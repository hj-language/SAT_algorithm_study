
## 2023-04-05 / 박준수 / PGS-구명보트


```python
from collections import deque

def solution(people, limit):
    answer = 0
    people_s = deque(sorted(people))
    
    while len(people_s) > 1:
        if(people_s[0] + people_s[-1] <= limit):
            people_s.popleft()
            people_s.pop()
            answer += 1
        else:
            people_s.pop()
            answer += 1
            
    if(people_s): answer += 1
    
    return answer
```

- 시간복잡도: O(n)
- 공간복잡도: O(n)
