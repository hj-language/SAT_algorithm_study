## 2023-04-05 / 이근탁 / PGS-체육복

#### 1차 시도 (FAILED)

```python
def solution(n, lost, reserve):
    for p in lost:
        if p in reserve:
            reserve.remove(p)
            lost.remove(p)
            
    for p in reserve:
        if p-1 in lost:
            lost.remove(p-1)
        elif p+1 in lost:
            lost.remove(p+1)
            
    return n-len(lost)
```

- 시간복잡도/공간복잡도: O(n)/O(n)
- 정확성 84
예외 테케 진짜 모르겠음
