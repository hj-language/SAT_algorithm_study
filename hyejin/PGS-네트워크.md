## 2023-04-14 / 김혜진 / PGS-네트워크

```python
def solution(n, computers):
    visited = [0]*n
    count = 0
    for i in range(n):
        if visited[i]: continue
        count += 1
        queue = [i]
        visited[i] = 1
        while queue:
            t = computers[queue.pop(0)]
            for u in range(len(t)):
                if t[u] and not visited[u]:
                    queue.append(u)
                    visited[u] = 1
    return count
```

- 시간복잡도/공간복잡도: O(n)
- 가장 기본적인 dfs/bfs 문제
