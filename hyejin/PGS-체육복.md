## 2023-04-03 / 김혜진 / PGS-체육복

#### 1차 시도 (FAILED)

```python
def solution(n, lost, reserve):
    for i, r in enumerate(reserve):
        if r in lost:
            reserve.pop(i)
            lost.pop(lost.index(r))
    answer = n - len(lost)
    for l in lost:
        if l-1 in reserve:
            answer += 1
            reserve.pop(reserve.index(l-1))
        elif l+1 in reserve:
            answer += 1
            reserve.pop(reserve.index(l+1))
    return answer
```

- 시간복잡도/공간복잡도: O(n\*m)/O(n+m) (n은 lost 길이, m은 reserve 길이)
- 정확성 72%

#### 2차 시도 (FAILED)

```python
def solution(n, lost, reserve):
    lost.sort()
    reserve.sort()
    for i, r in enumerate(reserve):
        if r in lost:
            reserve.pop(i)
            lost.pop(lost.index(r))
    answer = n - len(lost)
    for l in lost:
        if l-1 in reserve:
            answer += 1
            reserve.pop(reserve.index(l-1))
        elif l+1 in reserve:
            answer += 1
            reserve.pop(reserve.index(l+1))
    return answer
```

- 1차 시도에 lost, reserve 정렬
- 정확성 88%

#### 3차 시도

```python
def solution(n, lost, reserve):
    lost.sort()
    reserve.sort()
    _lost = [l for l in lost if l not in reserve]
    _reserve = [r for r in reserve if r not in lost]
    answer = n - len(_lost)
    for l in _lost:
        if l-1 in _reserve:
            answer += 1
            _reserve.pop(_reserve.index(l-1))
        elif l+1 in _reserve:
            answer += 1
            _reserve.pop(_reserve.index(l+1))
    return answer
```

- 2차 시도에 answer 에서 \_lost의 길이를 뺌
