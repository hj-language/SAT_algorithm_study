## 2023-04-05 / 김혜진 / PGS-피로도

```python
from itertools import permutations
def solution(k, dungeons):
    answer = 0
    pers = list(permutations(dungeons))
    for per in pers: # 순열 하나씩 탐색
        remain_prd = k
        tmp_count = 0
        for dengeon in per: # 던전 하나씩 탐색
            min_prd, consume_prd = dengeon
            if not (remain_prd >= min_prd and remain_prd - consume_prd >= 0):
                break
            tmp_count += 1
            remain_prd -= consume_prd
        answer = max(answer, tmp_count)
    return answer

print(solution(80, [[80,20],[50,40],[30,10]]))
```

- 시간복잡도/공간복잡도: O(n!/r!/(n-r)!)/O(n)
- 무식하게 모든 경우의 수 다 탐색하면 되는 문제였다.
