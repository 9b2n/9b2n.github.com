---
title: "Programmers : 프린터"
date: 2021-03-08 22:57:00 -0400
categories: CodingTest
---



### 🔒 [Programmers : 프린터](https://programmers.co.kr/learn/courses/30/lessons/42587)



priorities를 원형배열처럼 다뤄야할 것 같았다.

priorities의 원소를 popleft하고 append할 때마다 location도 함께 움직여야한다.

location을 움직일 때 원형배열인 것처럼 다루었다. 



### 🔑 코드

```python
from collections import deque
def solution(priorities, location):
    answer = 0
    temp = 0
    priorities = deque(priorities)
    while True:
        temp = priorities[0]
        if temp >= max(priorities):
            if location == 0:
                return answer + 1
            else:
                priorities.popleft()
                location = (len(priorities) + location - 1) % len(priorities)
                answer += 1
        else:
            priorities.popleft()
            priorities.append(temp)
            location = (len(priorities) + location - 1) % len(priorities)
```

~~중복되는 코드가 좀 있어서 줄이고 싶다~~

