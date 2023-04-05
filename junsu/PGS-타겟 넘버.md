## 2023-04-04 / 박준수 / PGS-타겟 넘버


```python
answer = 0

def dfs(i, result, target, numbers):
        global answer
        if i == len(numbers):
            if result == target:
                answer+=1

        else:
            dfs(i+1, result + numbers[i], target, numbers)
            dfs(i+1, result - numbers[i], target, numbers)

def solution(numbers, target):
    dfs(0,0,target,numbers)
    return answer

```

- 시간복잡도: O(2^n)
- 공간복잡도: O(n)
