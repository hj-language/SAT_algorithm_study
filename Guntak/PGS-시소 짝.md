## 2023-04-05 / 이근탁 / 시소 짝꿍

```python
def solution(weights):
    answer = 0
    
    dict = {}
    
    for i in weights:
        if i in dict:
            dict[i] += 1
        else:
            dict[i] = 1
    for i in dict:
        if dict[i] > 1:
            answer += (dict[i] * (dict[i]-1)) / 2
        if i*2 in dict:
            answer += dict[i] * dict[i*2]
        if i*2/3 in dict:
            answer += dict[i] * dict[i*2/3]
        if i*3/4 in dict:
            answer += dict[i] * dict[i*3/4]
    return answer
```

- 시간복잡도/공간복잡도: O(nlogn)/O(n)
