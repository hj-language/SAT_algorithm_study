## 2023-04-27 / 박준수 / PGS-개인정보 수집 유효기간


```python
def dateToDay(date):
    year, month, day = map(int, date.split("."))
    return (year * 12 * 28) + (month * 28) + day

def solution(today, terms, privacies):
    answer = []
    terms_arr  = [t.split() for t in terms]
    terms_dict = {t[0]:int(t[1]) for t in terms_arr}
    
    today_ = dateToDay(today)

        
    for i in range(len(privacies)):
        # print(today_)
        # print(dateToDay(i[:-2]))
        
        if(dateToDay(privacies[i][:-2]) + terms_dict[privacies[i][-1]]*28 <= today_ ):
            answer.append(i+1)
                          

    return answer

```

-   시간복잡도: O(n)
-   처음에는 모든 달이 28일이라는 것을 사용하지 못해서 해매버린...
-   반복문 돌 때  .index()를 사용하여 privacies의 중복을 알아채지 못해버린....
-   이게 레벨 1이라고요??
