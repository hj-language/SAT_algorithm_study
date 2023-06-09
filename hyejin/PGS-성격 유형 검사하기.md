## 2023-06-09 / 김혜진 / PGS-성격 유형 검사하기

```python
def solution(survey, choices):
    d = {"R": 0, "T": 0, "C": 0, "F": 0, "J": 0, "M": 0, "A": 0, "N": 0}
    for s, c in zip(survey, choices):
        if (c-4) > 0:
            d[s[1]] += (c-4)
        else:
            d[s[0]] += (4-c)
    answer = ''
    answer += "R" if d["R"] >= d["T"] else "T"
    answer += "C" if d["C"] >= d["F"] else "F"
    answer += "J" if d["J"] >= d["M"] else "M"
    answer += "A" if d["A"] >= d["N"] else "N"
    return answer
```

- 시간복잡도/공간복잡도: O(n)
- 단순 구현 문제. . 조금 더 잘 짜면 answer 구하는 로직을 예쁘게 만들 수 있겠지만 코딩테스트에서 그런건 사치 같은 ㅎㅎ
