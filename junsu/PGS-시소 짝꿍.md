## 2023-04-13 / 박준수 / PGS-시소 짝꿍

```python
from itertools import chain


def solution(weights):
    # 1:1, 2:3, 1:2, 3:4
    answer = 0
    weights_ = [[w ,w*2,w/2,(w*2)/3,(w*3)/2,(w*4)/3,(w*3)/4] for w in weights]
    weights_ = list(chain(*weights_))
    
    info = {key : 0 for key in weights_}

    for w in weights:
        answer += info[w] + info[w*2] + info[w/2] + info[(w*2)/3] + info[(w*3)/2] + info[(w*4)/3] + info[(w*3)/4]
        info[w] += 1
        
    return answer
```

-   시간복잡도/공간복잡도: O(n^2)/O(n)

- weights 리스트에 대해서 for 루프가 한 번 돌며 weights_ 리스트를 만들어내고, info 딕셔너리를 초기화합니다. 그 후에는 다시 weights 리스트에 대해서 for 루프를 돌며 info 딕셔너리를 업데이트하고, answer 값을 계산합니다.

	weights 리스트의 길이를 n이라고 하면, weights_ 리스트를 만드는 과정에서 weights 리스트를 7번 순회하므로 시간 복잡도는 O(7n) = O(n)입니다. 그러나 그 이후의 for 루프에서는 weights 리스트를 한 번 더 순회하므로 시간 복잡도는 O(n^2)입니다.

- weights_ 리스트는 weights 리스트와 동일한 길이를 가지며, 그 길이는 n입니다. info 딕셔너리는 weights_ 리스트에 들어가는 각 원소들의 등장 횟수를 저장하고 있으며, 이 딕셔너리의 크기는 weights_ 리스트에서 등장하는 원소들의 종류 수에 비례합니다.
	
	weights 리스트에서 모든 원소들이 서로 다르다고 가정할 때, weights_ 리스트의 길이는 7n이며, info 딕셔너리의 크기는 6n입니다. 따라서 전체적인 공간 복잡도는 O(7n + 6n) = O(n)입니다.
