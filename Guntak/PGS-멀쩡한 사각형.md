## 2023-04-13 / 이근탁 / PGS-멀쩡한 사각형


```python
import math

def solution(w,h):
    return w * h - (w + h - math.gcd(w,h))
```

- 시간복잡도: O(n)
