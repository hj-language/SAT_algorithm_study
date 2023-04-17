## 2023-04-11 / 김혜진 / PGS-괄호 변환

```python
def isValid(s):
    stack = []
    for c in s:
        if c == ")" and stack and stack[-1] == "(":
            stack.pop()
            continue
        stack.append(c)
    return len(stack) == 0

def split(s):
    left_count, right_count = 0, 0
    for i in range(0, len(s)):
        if s[i] == "(":
            left_count += 1
        else:
            right_count += 1
        if left_count == right_count:
            return s[:i+1], s[i+1:]

def reverse(s):
    answer = ""
    for c in s:
        if c == "(": answer += ")"
        else: answer += "("
    return answer

def solution(p):
    if len(p) == 0 or isValid(p): return p
    u, v = split(p)
    if isValid(u):
        return u+solution(v)
    else:
        return "("+solution(v)+")"+reverse(u[1:-1])
```

- 시간복잡도/공간복잡도: O(n log n)/O(n)
- 제시하는 알고리즘대로 구현만 할 수 있으면 됨
