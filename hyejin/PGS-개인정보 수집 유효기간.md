## 2023-04-25 / 김혜진 / PGS-개인정보 수집 유효기간

### 1차 시도 (실패)

```python
def add_month(date, month):
    date = list(map(int, date.split(".")))
    q, r = divmod(date[1]+month, 12)
    if r == 0: date[1] = 12
    else:
        date[0] += q
        date[1] = r
    date = list(map(str, date))
    return ".".join(date)

def is_expired(today, cmp):
    today_split = list(map(int, today.split(".")))
    cmp_split = list(map(int, cmp.split(".")))
    print(today_split, cmp_split)
    for i in range(3):
        if today_split[i] > cmp_split[i]: return True
        if today_split[i] < cmp_split[i]: return False
    return True # 날짜가 같으면 expired

def solution(today, terms, privacies):
    # {약관 종류: 유효기간} 저장
    terms_dict = {}
    for term in terms:
        kind, month = term.split(" ")
        terms_dict[kind] = int(month)
    # 개인정보 유효기간 확인
    answer = []
    for idx, privacy in enumerate(privacies):
        date, kind = privacy.split(" ")
        due = add_month(date, terms_dict[kind])
        if is_expired(today, due):
            answer.append(idx+1)
    return answer
```

- 시간복잡도/공간복잡도: O(n), O(n)
- 정확성 50%

### 2차 시도

```python
def add_month(date, month):
    date = list(map(int, date.split(".")))
    q, r = divmod(date[1]+month, 12)
    if r == 0:
        date[1] = 12
        date[0] += q-1
    else:
        date[0] += q
        date[1] = r
    date = list(map(str, date))
    return ".".join(date)
```

- r이 0일 때 q에 대한 처리를 해주지 않았음.
- ex) 수집 일자: 2022.11.01, 유효기간 13달 => 2023.12.01이 돼야 하는데 2022.12.01 이었다.
- 아래 풀이 참고해서 어느 부분이 틀린지 알게 됐다.

```python
def add_month(date, month):
    date = list(map(int, date.split(".")))
    date[1] += month
    while date[1] > 12:
        date[1] -= 12
        date[0] += 1
    date = list(map(str, date))
    return ".".join(date)
```
