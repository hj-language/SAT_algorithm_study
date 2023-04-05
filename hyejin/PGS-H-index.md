## 2023-04-05 / 김혜진 / PGS-H-index

#### 1차 시도 (FAILED)

```python
def solution(citations):
    citations.sort()
    answer = citations[0]
    for i in range(len(citations)):
        count = len(citations[i:])
        if count >= citations[i] and answer < count:
            answer = citations[i]
    return answer
```

- 시간복잡도/공간복잡도: O(n log n)/O(n)
- 정확성 12.5%

#### 2차 시도

```python
def solution(citations):
    citations.sort()
    answer = 0
    for h in range(0, len(citations)+1): #h는 논문 개수를 초과할 수 없음
        count = len(list(filter(lambda x: x >= h, citations)))
        answer = h if count >= h else answer
    return answer
```

- 질문하기 들어가서 반례 보고 풀었음.
- 문제를 잘못 읽어서 처음에는 무조건 [3, 0, 6, 1, 5]면 저 원소 중에 답이 있는 줄 알았음 .. **문제를 잘 읽자.**
- 반례
  - `[1, 4, 5]` => `2`
  - `[5, 6, 7]` => `3`
