## 2023-04-05 / 박준수 / PGS- H-Index


```python
def solution(citations):
    citations = sorted(citations, reverse=True)

    for i in range(len(citations)):
        if(i >= citations[i]):
            return i

    return len(citations)
```

- 시간복잡도: O(n^2)
- 공간복잡도: O(n)
- 처음보면 뭘 묻는지 감이 안오는 신기한 문제
