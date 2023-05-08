## 2023-05-04 / 이근탁 / 개인정보 수집 유효기간
```python
def convert_day(day):
    day = day.split(".")
    day = int(day[0]) * 12 * 28 + int(day[1]) * 28 + int(day[2])
    return day
 
def solution(today, terms, privacies):
    answer = []
    today = convert_day(today)
    terms = [term.split(" ") for term in terms]
    terms = dict(zip(list(zip(*terms))[0], list(zip(*terms))[1]))
    for idx, privacy in enumerate(privacies):
        day, term = privacy.split(" ")
        day = convert_day(day)
        day += (int(terms[term]) * 28)
        if today >= day:
            answer.append(idx + 1)
    return answer
```

- 시간복잡도/공간복잡도: O(n)
- 살짝 SQL Join 연산같은 zip 같은거 새로 써봤습니다.
