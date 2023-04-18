## 2023-04-18 / 김혜진 / PGS-테이블 해시 함수

```python
def solution(data, col, row_begin, row_end):
    data.sort(key=lambda x: (x[col-1], -x[0]))
    S_i_remain = [[d % (i+1) for d in data[i]] for i in range(row_begin-1, row_end)] # 각 컬럼을 i로 나눈 나머지들
    answer = 0
    for s in S_i_remain:
        answer ^= sum(s)
    return answer
```

- 시간복잡도/공간복잡도

```
먼저, data 리스트의 크기를 N이라고 가정합니다. data 리스트를 정렬하는데 사용되는 sort 메소드의 시간 복잡도는 최악의 경우 O(N log N)입니다.

그리고, S_i_remain 리스트를 생성하는데 필요한 계산 복잡도는 O(N^2)입니다. 이는 data 리스트의 모든 데이터에 대해서 각 컬럼 값에 대해 나머지를 계산해야 하기 때문입니다.

마지막으로, S_i_remain 리스트의 요소들을 이용하여 결과값을 계산하는데 필요한 계산 복잡도는 O(N)입니다. 이는 S_i_remain 리스트의 요소들을 순회하면서 XOR 연산을 수행하는 것이므로, 각 요소의 크기가 일반적으로 int 타입의 크기(32비트 또는 64비트)를 가지기 때문입니다.

따라서, 해당 알고리즘의 총 시간 복잡도는 O(N^2 + N log N)입니다.
```

- 제시하는 알고리즘대로 구현만 할 수 있으면 됨
