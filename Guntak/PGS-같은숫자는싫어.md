## 2023-04-05 / 이근탁 / 같은숫자는싫어

```python
def solution(arr):
    answer = []
    answer.append(arr[0])
    for i in arr:
        if(answer[len(answer)-1] != i):
            answer.append(i)
        else:
            continue
    return answer
```

- 시간복잡도/공간복잡도: O(n)/O(n)
