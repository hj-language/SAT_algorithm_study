## 2023-04-14 / 김혜진 / PGS-연속된 부분 수열의 합

### 1차 시도 (실패)

```python
def solution(sequence, k):
    sequence_sum = [0]
    for i in range(0, len(sequence)):
        sequence_sum.append(sequence[i]+sequence_sum[i])
    sequence.insert(0, 0)
    min_len = 1000000
    min_index = [0, 0]
    for i in range(1, len(sequence)):
        if sequence[i] == k: return [i-1, i-1]
        for j in range(i+1, len(sequence_sum)):
            if sequence_sum[j]-sequence_sum[i-1] == k and j-i < min_len:
                min_len = j-i
                min_index = [i-1, j-1]
    return min_index
```

- 시간복잡도/공간복잡도: O(n^2)/O(n)
- 정확성 44.1% (실패한 건 다 시간초과)

### 2차 시도 (실패)

```python
def solution(sequence, k):
    sequence.insert(0, 0)
    s, e = 1, 1
    answers = []
    while s <= e and s < len(sequence) and e < len(sequence):
        tmp = sum(sequence[s:e+1])
        if tmp == k:
            answers.append((s-1, e-1))
            e += 1
        elif tmp < k: e += 1
        else: s += 1
    answers.sort(key=lambda x: (x[1]-x[0], x[0]))
    return answers[0]
```

- 반복문을 1번만 한다는 점에서는 줄였지만, sum을 구하면 또 최대 n만큼 반복될 수 있음 => O(n^2)
- 정확성 23.5% (시간초과)

### 3차 시도

```python
def solution(sequence, k):
    sequence_sum = [0]
    for i in range(0, len(sequence)):
        sequence_sum.append(sequence[i]+sequence_sum[i])
    sequence.insert(0, 0)
    s, e = 0, 1
    answers = []
    while s <= e and s < len(sequence) and e < len(sequence):
        tmp = sequence_sum[e]-sequence_sum[s]
        if tmp == k:
            answers.append((s, e-1))
            e += 1
        elif tmp < k: e += 1
        else: s += 1
    answers.sort(key=lambda x: (x[1]-x[0], x[0]))
    return answers[0]
```

- 투포인터 + 미리 합 구해놓기.
