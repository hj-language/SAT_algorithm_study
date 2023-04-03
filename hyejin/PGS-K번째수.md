## 2023-04-03 / 김혜진 / PGS-K번째수

```python
    def solution(array, commands):
        answer = []
        for command in commands:
            i, j, k = command
            answer.append(sorted(array[i-1:j])[k-1])
        return answer
```

- 시간복잡도/공간복잡도: O(nlogn\*m)/O(n+m)
- 파이썬 sorted, sort의 시간복잡도는 O(n log n)이다. Timsort라는 정렬 알고리즘을 쓰는데, 평균/최악 모두 O(nlogn)을 보장한다고 한다. ([Reference](https://www.codeit.kr/community/questions/UXVlc3Rpb246NjBlNTg4NzIwN2Y2YzI0MzY1YmQ4Mzkw))
