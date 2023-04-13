## 2023-04-03 / 김혜진 / PGS-최소직사각형

```python
    def solution(sizes):
        for size in sizes:
            size.sort()
        row = max(sizes, key=lambda n: n[0])[0]
        col = max(sizes, key=lambda n: n[1])[1]
        return row*col
```

- 시간복잡도/공간복잡도: O(nlogn)/O(n)
- sort가 nlogn, max가 n이기 때문에 O(nlogn)으로 잡았다.
