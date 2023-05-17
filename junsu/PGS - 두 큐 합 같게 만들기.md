
# 2023-05-17 / 박준수 / PGS - 두 큐 합 같게 만들기


# Complexity

- Time complexity(alternative ver.):  $$O(n)$$


- Space complexity: $$O(n)$$


# Code

```python
from collections import deque

def solution(queue1, queue2):
    answer = 0    
    q1 = deque(queue1)
    q2 = deque(queue2)
    
    sum1 = sum(queue1)
    sum2 = sum(queue2)
    
    # 홀수인 경우
    if (sum1 + sum2) % 2 != 0:
        return -1
    
    while True:
        
        # 전체 배열의 길이가 2n이므로, 한 포인터 당 최대 2n번의 이동이 필요합니다.
        # 따라서, 총 4n만큼의 작업을 수행한 뒤에도 두 큐의 합을 같게 만들지 못했다면 
        # 그 이후에는 이미 탐색했던 구간을 다시 탐색하는 것이므로 의미가 없습니다
        if answer == 4 * len(queue1):
            return -1
        
        if sum1 > sum2:
            value = q1.popleft()
            q2.append(value)
            sum1 -= value
            sum2 += value
            
        elif sum1 < sum2:
            value = q2.popleft()
            q1.append(value)
            sum1 += value
            sum2 -= value
            
        else:
            return answer
        
        answer += 1
```
