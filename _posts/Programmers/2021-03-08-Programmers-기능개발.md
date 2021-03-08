---
title: "Programmers : 기능개발"
date: 2021-03-08 22:16:00 -0400
categories: CodingTest
---

### 🔒 [Programmers : 기능개발](https://programmers.co.kr/learn/courses/30/lessons/42586)


progresses 리스트를 앞에서부터 순회하면 되는 문제이다.

진도율이 100이면 끝이므로, progresses의 원소를 하나씩 볼 때마다 100에서 뺀 값을 그 작업의 진행속도로 나누면 며칠(days)을 작업하는 지 알 수 있다.

작업일 만큼 뒤의 값들도 원래 값(progresses[i]) + speeds[i]*days 해준다.

이 작업을 리스트의 원소 수 만큼 반복하면 끝이다.



### 🔑 코드

```python
from math import ceil
from collections import deque
def solution(progresses, speeds):
    answer = []
    progresses = deque(progresses)
    speeds = deque(speeds)
    cnt = 1

    while progresses:
        p = progresses.popleft()
        s = speeds.popleft()
        if p >= 100:
            cnt += 1
        else:
            answer.append(cnt)
            cnt = 1
            n = ceil((100-p)/s)
            for i in range(len(speeds)):
                progresses[i] += speeds[i]*n
    answer.append(cnt)

    return answer[1:]
```

작업의 통일성을 주기 위해 처음 확인할 때도 answer에 값을 넣어주었고, answer을 return할 때는 인덱스를 1부터 시작하여 반환했다.