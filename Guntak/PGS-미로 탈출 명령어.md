## 2023-05-12 / 이근탁 / 미로 탈출 명령

```python
def distance(x, y, r, c):
    return abs(x - r) + abs(y - c)

def solution(n, m, x, y, r, c, k):
    if (k - distance(x, y, r, c)) % 2 or k < distance(x, y, r, c):
        return "impossible"
    answer = ""
    move = 0
    
    while x < n and (k - move) > distance(x, y, r, c):
        move += 1
        x += 1
        answer += "d"
    
    while 1 < y and (k - move) > distance(x, y, r, c):
        move += 1
        y -= 1
        answer += "l"
        
    while (k - move) > distance(x, y, r, c):
        move += 2
        answer += "rl"
    
    if x < r:
        answer += "d" * (r - x)
        x = r
    if y > c:
        answer += "l" * (y - c)
        y = c
    if y < c:
        answer += "r" * (c - y)
        y = c
    if x > r:
        answer += "u" * (x - r)
        x = r
    return answer
```

- 시간복잡도/공간복잡도: O(n+m)
