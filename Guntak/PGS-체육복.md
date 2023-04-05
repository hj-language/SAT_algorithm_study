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

2058 예외 딱 알았음
체육복 빌려주는 차례가 앞-> 뒤인지, 뒤 -> 앞인지에 따라 달라짐
ex) 
lost = [1,3]
reserve = [2, 4]

1) 차례가 앞뒤면 12345 가능
2) 차례가 뒤앞이면 2345 가능이라 다름

-> 즉 1,2 연산을 하고 이 두 개중 큰게 
