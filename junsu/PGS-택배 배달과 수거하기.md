## 2023-05-04 / 박준수 / PGS-택배 배달과 수거하기


```python
def solution(cap, n, deliveries, pickups):
    
    # 배달과 수거를 분리하여 생각 
    # 집별로 거리, 배달, 수거를 묶기
    # 배달 수거를 zip
    # 거리 까지 enumerate 시작 index 1
    # 배달 혹은 수거할 상자가 있는 경우만 고려
    idps = [(i,d,p) for i,(d,p) in enumerate(zip(deliveries, pickups), 1) if d or p]
    answer = 0
    
    # 한번의 이동에 cap만큼만 배달, 수거가 가능
    # 얼마나 배달 ,수거했는지 변수 저장
    delivery = 0
    pickup = 0
    
#     print(idps)
    
    while idps:
        i,d,p = idps.pop() # 가장 먼 집부터 => pop
        delivery += d
        pickup += p
        
        
#         두 변수 중 하나라도 존재 할 경우 이 집까지 이동해야 하므로
#         양수가 있는지 체크
#         둘다 0이하가 될때까지 이동

#         집거리 i, 왕복하면 2*i
#         이동하면서 cap만큼 배달, 수거 가능하니 각각 cap만큼 감소
        
        while delivery > 0 or pickup >0:
            delivery -= cap
            pickup -= cap
            answer += 2*i
            
    return answer



```

-   시간복잡도: O(n^2)
-   공간복잡도: O(n)
-   이게 레벨 2이라고요??


## cf. 소개하고 싶은 코드

1. DP를 이용한 풀이 
```python
def solution(cap, n, deliveries, pickups) :
    space = [[0,0] for _ in range(n+1)]
    startD, startP = cap, cap
    distance = 0
    count = 0
    for i in range(n-1, -1, -1):
        nowD, nowP = deliveries[i], pickups[i]
        space[i][0] = space[i+1][0] - nowD
        space[i][1] = space[i+1][1] - nowP
        if space[i][0] < 0 or space[i][1] < 0 : 
            goBack = ((i+1)*2)
            while True :
                if space[i][0] >= 0 and space[i][1] >= 0 :
                    break
                space[i][0] += cap
                space[i][1] += cap
                count += 1
            distance += goBack * count
            count = 0
    return distance

```



2. 신기한 풀이
```python
from itertools import zip_longest as zip

def tolist(l):
    n=[]
    for i,d in enumerate(l):
        for _ in range(d):
            n.append(i+1)
    return n

def solution(cap, n, deliveries, pickups):
    d=tolist(deliveries)
    p=tolist(pickups)
    d.reverse()
    p.reverse()
    d=d[::cap]
    p=p[::cap]
    
    return 2*sum([max(x,y) for x,y in zip(d,p,fillvalue=0)])
```


3. 짧은 greedy 풀이
```python
def solution(cap, n, deliveries, pickups):
    deliveries = deliveries[::-1]
    pickups = pickups[::-1]
    answer = 0

    have_to_deli = 0
    have_to_pick = 0

    for i in range(n):
        have_to_deli += deliveries[i]
        have_to_pick += pickups[i]

        while have_to_deli > 0 or have_to_pick > 0:
            have_to_deli -= cap
            have_to_pick -= cap
            answer += (n - i) * 2

    return answer
```
