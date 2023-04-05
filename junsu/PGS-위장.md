## 2023-04-05 / 박준수 / PGS-위장


```python
def solution(clothes):
    answer = 1
    clothDic = {i[1] : [t[0] for t in clothes if t[1] == i[1]] for i in clothes}
    
    for i in clothDic.keys():
        answer *= len(clothDic[i]) + 1
        
    return answer - 1
```

- 시간복잡도: O(n)
- 공간복잡도: O(n)
