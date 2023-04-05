## 2023-04-04 / 박준수 / PGS-기능개발


```python
def solution(progresses, speeds):
    days = []
    res = []
    
    for p,s in zip(progresses, speeds):
        prog = p
        cnt = 0
        while True:
            prog += s
            cnt += 1
            if prog >= 100:
                days.append(cnt)
                break
                
    curr = 0
    ptr = 1
    c = 1
    while True:
        if ptr >= len(days):
            res.append(c)
            break
            
        if days[curr] < days[ptr]:
            res.append(c)
            c = 1
            curr = ptr
            ptr = curr + 1
            continue
            
        else:
            c += 1
            ptr += 1
	  
    return res
```

- 시간복잡도: O(n^2)
- 공간복잡도: O(n)
- 2019년 소프트웨어분석및설계시간에 풀었던 코드


