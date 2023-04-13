## 2023-04-04 / 박준수 / PGS-더 맵게

### 1차 시도(FAILED)
```python
def solution(scoville, K):
    answer = 0
    scoville_s = sorted(scoville,reverse=True)
    
    while scoville_s[-1] < K:
        if len(scoville_s)>1:
            answer += 1
            least = scoville_s.pop()
            second = scoville_s[-1]
            if least > second:
                scoville_s[-1] = least * 2 + second
            else:
                scoville_s[-1] = least + second * 2
            scoville_s.sort(reverse=True)
            
        else:
            return -1
        
    return answer
```

- 시간복잡도: O(n)
- 공간복잡도: O(n)
- 정확도: 100
- 효율성: 0 (시간 초과)   
