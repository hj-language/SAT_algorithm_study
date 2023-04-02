## 2023-04-02 / 김혜진 / PGS-같은 숫자는 싫어

#### 1차 시도 (FAILED)

```python
    def solution(arr):
        answer = []
        while arr:
            answer.append(arr[0])
            flag = False
            for i in range(1, len(arr)):
                if arr[i] != answer[-1]:
                    flag = True
                    break
            arr = arr[i:] if flag else arr[i+1:]
        return answer
```

- 시간복잡도/공간복잡도: O(n^2)/O(n)
- 정확성 만점, 효율성 0점

#### 2차 시도 (FAILED)

```python
    def solution(arr):
        i = 0
        while i < len(arr) - 1:
            if arr[i] == arr[i+1]:
                arr.pop(i)
            else:
                i += 1
        return arr
```

- 시간복잡도/공간복잡도: O(n)/O(n)
- 정확성 만점, 효율성 0점

#### 3차 시도

```python
    def solution(arr):
    answer = [arr[0]]
    for a in arr:
        if a != answer[-1]:
            answer.append(a)
    return answer
```

- 시간복잡도/공간복잡도: O(n)/O(n)
- 스택/큐 문제라고 뜨길래 복잡한 게 있나 싶었는데 그냥 1단계다.
