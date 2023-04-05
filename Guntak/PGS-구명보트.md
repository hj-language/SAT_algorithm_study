## 2023-04-05 / 이근탁 / PGS-구명보트

#### 1차 시도 (FAILED) -> 문제 제대로 안 읽음 ㅡㅡ

```python
def solution(people, limit):
    answer = 0
    people = sorted(people, reverse = True)
    while people != []:
        left = limit
        onboat = []
        for person in people:
            if person <= left:
                left -= person
                onboat.append(person)
        for s in onboat:
            people.remove(s)
        answer += 1
    return answer
```

보트에 최대 2명이라는걸 못 봄

```python
def solution(people, limit):
    answer = 0

    people = sorted(people)
    l = 0
    r = len(people)-1

    while l <= r:
        if people[l] + people[r] > limit:
            answer += 1
            r -= 1
        else:
            answer += 1
            r -= 1
            l += 1

    return answer
```

- 시간복잡도/공간복잡도: O(n log n)/O(n)
