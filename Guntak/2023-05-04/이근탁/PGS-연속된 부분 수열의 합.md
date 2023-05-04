## 2023-05-04 / 이근탁 / 연속된 부분 수열의 합

```python
def solution(sequence, k):
    answers = []
    sum = 0
    front = 0
    rear = -1
    
    while True:
        if sum < k:
            rear += 1
            if rear >= len(sequence):
                break
            sum += sequence[rear]
        else:
            sum -= sequence[front]
            if front >= len(sequence):
                break
            front += 1
        if sum == k:
            answers.append([front, rear])
    
    answers.sort(key=lambda x: (x[1]-x[0], x[0]))
    return answers[0]
```

- 시간복잡도/공간복잡도: O(n)
- 투포인터 실제로 문제 적용해보니까 신기하네용
