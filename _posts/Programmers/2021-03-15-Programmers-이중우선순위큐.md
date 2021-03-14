---
title: "Programmers : 이중우선순위큐"
date: 2021-03-15 01:21:00 -0400
categories: CodingTest
---



### 🔒 [Programmers : 이중우선순위큐](https://programmers.co.kr/learn/courses/30/lessons/42628)

<hr>

이 문제는 heap으로 풀려고 발악을 했던 문제다🤣

문제를 풀다보니 deque로 풀면 너 낫지 않았을까? 하다가 나의 풀이에 이용된 두 자료구조의 시간 복잡도를 비교해보았다.

원소의 삽입에서 heap은 **logn** 시간, deque는 **1** 이지만, 정렬까지 한다면 **nlogn**시간이 걸린다.

즉 삽입 : **heap < deque**

최소값 삭제에서 heap은 **logn**시간, deque는 **1** 이므로 **heap > deque**

최대값 삭제에서 heap은 최대힙으로 바꾸는 시간 n, 최대값 삭제 시간 logn, 최소힙으로 바꾸는 시간 n이므로 **n** 이다.

하지만 deque는 **1** 이다. 그러므로 최대값 삭제 : **heap > depue**

입력만 한다고 가정하면 힙으로 구현한 풀이가 더 짧지만, 같은 수의 입력과 최대값 삭제가 이루어진다면 deque로 구현한 풀이가 더 빠르다.

아마 나의 풀이가 최선의 풀이보다 비효율적으로 풀어서인 것 같다😂 heap을 이용한 더 좋은 방법이 있는지 고민해봐야겠다.

<hr>


### 🔑 코드

```python
from heapq import heappop, heappush
def solution(operations):
    heap = []
    for string in operations:
        op, num = string.split()
        temp = []
        if op == 'I':
            heappush(heap, int(num))
        elif op == 'D' and heap:
            if num == '1':
                for _ in range(len(heap)):
                    heappush(temp, -heappop(heap))
                heappop(temp)
                for _ in range(len(temp)):
                    heappush(heap, -heappop(temp))
            else:
                heappop(heap)
    if not heap:
        return [0,0]
    else:
        minh = heap[0]
        temp = []
        for _ in range(len(heap)):
            heappush(temp, -heappop(heap))
        return [-temp[0], minh]
```

처음엔 최소힙과 최대힙 둘 다 이용하여 풀려고 했으나,
최대값 삭제와 최소값 삭제가 이루어질 때 동기화를 해줘야하는 문제가 있었다.

그래서 동기화를 해주나, 최대힙으로 바꾸고 최소힙으로 다시 바꾸나 둘 다 똑같은 시간이 걸리기 때문에
최소힙으로만 구현을 했다.

우선 I가 입력되면 최소힙에 원소를 추가한다.

D가 입력되고 1이 입력되면 최대값을 삭제해야하므로 최대힙으로 바꾸고 최대값을 삭제해준 뒤, 최소힙으로 다시 바꾼다.

D가 입력되고 -1이 입력되면 최소값을 삭제해준다.

마지막 반환할 때는 heap이 비어있으면 [0,0]을 반환하고,

비어있지 않다면 최소값을 먼저 얻고, 최대힙으로 바꾼후 최대값을 얻어 [최대값, 최소값]을 반환해주었다.