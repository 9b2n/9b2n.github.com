---
title: "Programmers : 더 맵게"
date: 2021-03-15 00:44:00 -0400
categories: CodingTest
---



### 🔒 [Programmers : 더 맵게](https://programmers.co.kr/learn/courses/30/lessons/42626)

<hr>

힙을 사용할 줄 안다면 쉽게 풀 수 있는 문제였다.

두 개의 음식을 섞어 스코빌 지수를 높이는 작업마다 목록에서 스코빌 지수가 제일 작은 음식 두 개를 빼내서 조합하면 되므로

최소힙을 이용하여 풀었다.



<hr>


### 🔑 코드

```python
import heapq
def solution(scoville, K):
    answer = 0
    heap = []
    for i in scoville:
        heapq.heappush(heap, i)

    for _ in range(len(heap)):
        a = heapq.heappop(heap)
        if a >= K:
            return answer
        if not heap:
            return -1
        b = heapq.heappop(heap)
        c = a + b * 2
        heapq.heappush(heap, c)
        answer += 1
```

최소 힙을 이용하므로 heappop을 한 값은 제일 작은 값이므로 이 값이 K보다 크다면 현재까지 작업했던 횟수를 반환한다.

heap이 비어있다면 더이상 스코빌 지수를 올릴 수 있는 수단이 없으므로 -1을 반환한다.

그게 아니라면 heappop하여 2번째로 작은 스코빌 지수의 음식을 섞는다. 섞은 결과를 다시 목록에 추가한다.

모든 음식의 스코빌 지수가 K를 넘게 하는 작업의 최소 횟수를 반환해야 하므로 섞는 작업을 할 때마다 횟수를 카운트한다.