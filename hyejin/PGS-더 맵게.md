## 2023-04-04 / 김혜진 / PGS-더 맵게

#### 1차 시도 (FAILED)

```python
def solution(scoville, K):
    answer = 0
    while min(scoville) < K:
        if len(scoville) == 1: return -1
        answer += 1
        scoville.sort()
        a = scoville.pop(0)
        b = scoville.pop(1)
        scoville.append(a+b*2)
    return answer
```

- 시간복잡도/공간복잡도: O(n^2 log n)/O(n)
- 정확성 32.3점, 효율성 0점

#### 2차 시도 (FAILED)

```python
def solution(scoville, K):
    answer = 0
    while min(scoville) < K:
        if len(scoville) == 1: return -1
        answer += 1
        scoville.sort()
        a = scoville.pop(0)
        b = scoville.pop(0)
        scoville.append(a+b*2)
    return answer
```

- 1차 시도에서 멍청하게도 두번째로 낮은거 pop 할 때 1번째를 해버렸다.
- 고쳤지만 시간 초과가 떴다.
- 정확성 100%, 효율성 0점

#### 3차 시도 (FAILED)

```python
import heapq
def solution(scoville, K):
    answer = 0
    heapq.heapify(scoville)
    while min(scoville) < K:
        if len(scoville) == 1: return -1
        answer += 1
        a = heapq.heappop(scoville)
        b = heapq.heappop(scoville)
        heapq.heappush(scoville, a+b*2)
    return answer
```

- 시간복잡도: O(n)
- 리스트 sort 하는 대신 heap 써서 이용했는데도 시간 초과가 떴다.
- 정확성 100%점, 효율성 0점

#### 4차 시도

```python
import heapq
def solution(scoville, K):
    answer = 0
    heapq.heapify(scoville) # list -> heap 변환 O(n)에 해줌.
    while scoville[0] < K:
        if len(scoville) == 1: return -1
        answer += 1
        a = heapq.heappop(scoville) # 제일 작은 값 (0번째 값) pop
        b = heapq.heappop(scoville)
        heapq.heappush(scoville, a+b*2) # 값을 적절한 위치에 push
    return answer
```

- 아무리 봐도 모르겠어서 질문하기 들어가서 보고 해결함.
- scoville에서 min값을 찾을 때, 최소힙을 이용하면 0번째가 최솟값이기 때문에 O(n)으로 min() 써서 찾을 필요가 없다.
