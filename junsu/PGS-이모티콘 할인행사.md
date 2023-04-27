## 2023-04-27 / 박준수 / PGS-이모티콘 할인행사


```python
from itertools import product

def solution(users, emoticons):
    rate = [10,20,30,40]
    plus_user = 0
    max_price = 0

    discounts = product(rate, repeat=len(emoticons))
    
    for dis in discounts:
        _user = 0
        _sum = 0
        
        for u in users:
            temp = 0 # 지불 금액
            
            for i in range(len(emoticons)):
                if dis[i] >= u[0]:
                    temp += emoticons[i] * (100 - dis[i]) // 100

            if temp >= u[1]:
                _user += 1
            else:
                _sum += temp
                
        if plus_user < _user:
            plus_user = _user
            max_price = _sum
            
        if plus_user == _user:
            if max_price < _sum:
                max_price = _sum
                    
    
    return [plus_user,max_price]
```

- 시간복잡도: O(4^n × n × m)
- `from itertools import product`를 아셨습니까? 저는 잘 몰랐습니다.

### From Kakao Tech Blog
[출처] https://tech.kakao.com/2023/01/25/2023-kakao-recruitment-round-1/  
이것은 사용자 수를 n, 이모티콘 수를 m이라 했을 때, 간단한 반복문과 조건문을 통해서 O(n × m)에 구할 수 있습니다.
각 사용자가 이모티콘 구매에 돈을 얼마를 쓰는지 구합니다. 이모티콘 구매 비용이 기준 비용보다 더 든다면, 구매 비용을 0으로 만들고 이모티콘 플러스 가입자 수에 1을 더해줍니다. 
그렇지 않다면 이모티콘 판매액에 비용을 더해줍니다.
이모티콘에 할인율을 적용하는 모든 경우의 수에 대해서 이 과정을 반복한다면... 
