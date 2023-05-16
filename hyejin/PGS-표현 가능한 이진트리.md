## 2023-05-12 / 김혜진 / PGS-표현 가능한 이진트리

### 1차 시도 (실패)

```python
import math

def recursive(number, count):
    if len(number) == 1 and count == 0:  return 1
    if len(number) % 2 == 0:
        number = '0'+number
    if number[len(number)//2] == '0': return 0
    left = number[:len(number)//2]
    right = number[len(number)//2+1:]
    return min(recursive(left, count-1), recursive(right, count-1))

def solution(numbers):
    answer = []
    for number in numbers:
        binary = bin(number)[2:]
        tree_height = math.ceil(math.sqrt(len(binary)))
        tmp = recursive(binary, tree_height-1)
        answer.append(tmp)
    return answer
```

- TC 20개 중 1번 빼고 다 실패

### 2차 시도 (실패)

```python
import math

def recursive(number):
    if len(number) == 1: return 1

    left = number[:len(number)//2]
    right = number[len(number)//2+1:]

    if number[len(number)//2] == '0':
        if (left and left[len(left)//2] == '1') or (right and right[len(right)//2] == '1'):
            return 0

    return min(recursive(left), recursive(right))

def solution(numbers):
    answer = []
    for number in numbers:
        binary = bin(number)[2:]
        tree_height = math.ceil(math.sqrt(len(binary)))
        tree_max = pow(2, tree_height)-1
        binary = "0"*(tree_max-len(binary)) + binary
        tmp = recursive(binary)
        answer.append(tmp)
    return answer
```

- 1번 시도에서는 현재 2진수 길이가 짝수이면 0을 더했는데, 그게 아니라 처음부터 포화이진트리를 만들기 위해 0을 다 채움
- TC 1, 3 빼고 다 실패 (런타임에러 포함)

- TT
