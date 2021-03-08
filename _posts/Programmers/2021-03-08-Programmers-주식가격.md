---
title: "Programmers : 주식가격"
date: 2021-03-08 15:08:00 -0400
categories: CodingTest
---

### 🔒 [Programmers : 주식가격](https://programmers.co.kr/learn/courses/30/lessons/42584)


이 문제는 현재 인덱스를 기준으로 다음 인덱스부터 훑어서 현재 값보다 작은 값이 나타나면 그 값의 인덱스에 현재 인덱스를 빼주면 되는 간단한 문제이다.

나는 거꾸로 prices 리스트의 끝부분부터 탐색을 시작했다.



### 🔑 코드

```python
from collections import deque
def solution(prices):
    result = deque([])

    for i in range(len(prices)-1,-1,-1):
        if not result :
            result.appendleft(len(result))
            continue
        
        cnt = 0
        for j in range(i+1,len(prices)):
            cnt += 1
            if prices[i] > prices[j]:
                break
        result.appendleft(cnt)

    return list(result)
```

처음 접근했을 때, 뒤부터 탐색하면 좀만 더 빠르지 않을까? 라는 생각에서 코딩을 했으나

시간계산을 해보니 그냥 똑같았다. 타이핑을 더 하는 고생을 한 거 같다 ...😂

이 문제를 풀고서 O(n)시간의 실행시간을 갖는 풀이 방법을 고민하였으나 논리 오류로 막히고 말았다..🤔

천천히 더 고민해봐야겠다 ..

