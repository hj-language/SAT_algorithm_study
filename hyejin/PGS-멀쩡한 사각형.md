## 2023-04-11 / 김혜진 / PGS-멀쩡한 사각형

```python
def gcd(a, b):
    a, b = min(a, b), max(a, b)
    while a != 0:
        a, b = b%a, a
    return b

def solution(w,h):
    return w*h - (w+h-gcd(w, h))
```

- 시간복잡도/공간복잡도: O(1)/O(1)
