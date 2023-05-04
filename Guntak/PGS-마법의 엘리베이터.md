## 2023-05-04 / 이근탁 / 마법의 엘리베이터

```python
def solution(storey):
    answer = 0
    while storey!=0:
        answer += (storey%10 if 5 > storey%10 else 10-storey%10)
        if (storey%10==5 and storey%100>=50) or (storey%10>5):
            storey+=10
        storey//=10
    return answer
```

- 시간복잡도/공간복잡도: O(logn) (상용로그임)
