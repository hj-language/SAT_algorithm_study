## 2023-04-04 / 김혜진 / PGS-기능개발

```python
import math
def solution(progresses, speeds):
    END = 100
    answer = []
    remain_days = []
    for p, s in zip(progresses, speeds):
        remain_days.append(math.ceil((END-p)/s))
    i = 0
    while i < len(remain_days):
        j = i + 1
        while j < len(remain_days) and remain_days[i] >= remain_days[j]:
            j += 1
        answer.append(j-i)
        i = j
    return answer
```

- 시간복잡도/공간복잡도: O(n^2)/O(n)
- 처음에 >=를 >로 해서 정확성 63.6% 뜸
- `zip`: 길이가 같은 여러 리스트에서 아이템 하나씩 뽑아올 때 사용
- 나눈 결과 올림을 위해 math.ceil(a//b) 대신 -(-a//b)를 쓸 수 있다고 함! [(참고)](https://velog.io/@choiyunh/%EC%98%AC%EB%A6%BC%EB%B0%98%EC%98%AC%EB%A6%BC%EB%82%B4%EB%A6%BC%EB%B2%84%EB%A6%BC)
