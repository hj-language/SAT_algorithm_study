## 2023-04-04 / 김혜진 / PGS-위장

#### 1차 시도 (FAILED)

```python
from itertools import combinations

def solution(clothes):
    clothes_dict = {}
    for [nm, tp] in clothes:
        if tp not in clothes_dict:
            clothes_dict[tp] = [nm]
        else:
            clothes_dict[tp].append(nm)
    kind_list = clothes_dict.keys()
    kind_no = len(kind_list)
    answer = 0
    for i in range(1, 1+kind_no):
        combi_list = combinations(kind_list, i)
        for combi in combi_list:
            tmp = 1
            for c in combi:
                tmp *= len(clothes_dict[c])
            answer += tmp
    return answer
```

- 시간복잡도/공간복잡도: O(n!/r!/(n-r)!)/O(n)
- tc1에서 시간초과남
- 정확성 96.4%

#### 2차 시도

```python
def solution(clothes):
    clothes_dict = {}
    for nm, tp in clothes:
        if tp not in clothes_dict:
            clothes_dict[tp] = 1
        else:
            clothes_dict[tp] += 1
    answer = 1
    for tp in clothes_dict:
        answer *= clothes_dict[tp] + 1
    return answer - 1
```

- 시간복잡도/공간복잡도: O(n)
- combination 쓰는 것도 좋았지만 좀 더 수학적으로 접근해야 했다..
