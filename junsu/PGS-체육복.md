## 2023-04-04 / 박준수 / PGS-체육복


```python
def solution(n, lost, reserve):
    lost_ = sorted([i for i in lost if i not in reserve])
    reserve_ = sorted([i for i in reserve if i not in lost])

    cnt = 0
    for i in lost_:
        if i - 1 in reserve_:
            cnt += 1
            reserve_.remove(i - 1)
            continue
        if i + 1 in reserve_:
            cnt += 1
            reserve_.remove(i + 1)
            continue
            
    return n - len(lost_) + cnt
```

- 시간복잡도: O(n)
- 공간복잡도: O(n)
