---
title: "Programmers : 다리를 지나는 트럭"
date: 2021-03-08 15:03:00 -0400
categories: CodingTest
---

### 🔒 [Programmers : 다리를 지나는 트럭](https://programmers.co.kr/learn/courses/30/lessons/42583)


이 문제를 보고 **현재 다리 상황을 나타내는 큐**와 **대기 중인 트럭 상황을 나타내는 큐**가 필요하다고 생각했다. 

그래서 파라미터로 전달되는 truck_weights를 deque로 바꿔주고, 현재 다리 상황을 나타내는 큐인 bridge를 다리의 길이 만큼 0으로 초기화 시켜주었다.

bridge는 1초마다 하나 씩 밀리는 형태가 되고 이를 이용하여 문제를 풀었다.



### 🔑 코드

```python
from collections import deque
def solution(bridge_length, weight, truck_weights):
    answer = 0
    bridge = [0] * bridge_length
    truck_weights = deque(truck_weights)
    bridge = deque(bridge)
    sumBridge = 0
    
    while truck_weights or sumBridge:
        if truck_weights and sumBridge + truck_weights[0] <= weight:
            bridge.appendleft(truck_weights.popleft())
        else:
            bridge.appendleft(0)
        bridge.pop()

        sumBridge += bridge[0] - bridge[bridge_length-1]
        answer += 1

    return answer + 1
```

대기 중인 트럭이 모두 없고, 다리 안에 차가 없을 때 종료되도록 했다.

현재 다리의 무게(**sumBridge**) 처음 sum(bridge)로 했으나 반복문이 돌 때마다는 bridge를 순회하는 것이 매우 비효율적일 것 같아서

1초가 지날 때마다 다리의 첫번째 무게를 더해주고 마지막 무게를 빼주어 구했다.

while문 마지막에는 1초가 흐르지 않으므로 return에서 answer에 1초를 더해주었다.