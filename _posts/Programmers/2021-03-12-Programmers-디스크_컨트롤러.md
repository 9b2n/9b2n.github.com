---
title: "Programmers : 디스크 컨트롤러"
date: 2021-03-12 11:43:00 -0400
categories: CodingTest
---



### 🔒 [Programmers : 디스크 컨트롤러](https://programmers.co.kr/learn/courses/30/lessons/42627)

<hr>

운영체제에서 스케줄링 알고리즘에 관련된 문제이다.

운영체제를 공부했더라면 낯익은 문제일 것이다.



<hr>


### 🔑 코드

```python
from heapq import heapify, heappop, heappush
def solution(jobs):
    answer = 0
    cur, cnt = 0, len(jobs)
    heap = []
    heapify(jobs)
    while jobs or heap:

        while jobs:
            if jobs[0][0] > cur:
                break
            enter, processing = heappop(jobs)
            heappush(heap, (processing, enter))

        if not heap: # 남은 작업이 현재 시간 후에 들어오는 작업들만 남음
            enter, processing = jobs[0]
            cur = enter
            continue

        p, e = heappop(heap)
        answer += cur - e + p
        cur += p
        
    return answer//cnt
```

1. **현재 시간(cur) 이하**의 시간에서 요청이 들어온 작업들을 힙에 넣는다. 힙에 넣을 때는 **작업 시간**을 기준으로 min heap이 된다. 

2. 힙이 비었으나 요청될 작업이 남아있을 경우 **현재 시간**을 **jobs**의 제일 가까운 요청시간으로 이동하여 1번을 다시 한다.

3. heap을 pop한 것을 계산한다.
4. **heap**과 **jobs**가 빌 때까지 반복한다.

