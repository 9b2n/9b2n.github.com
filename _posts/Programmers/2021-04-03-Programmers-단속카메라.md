---
title: "Programmers : 단속카메라"
date: 2021-04-03 01:08:00 -0400
categories: CodingTest
---
-


### 🔒 [Programmers : 단속카메라](https://programmers.co.kr/learn/courses/30/lessons/42884)

<hr>

이 문제 조건에서 차량의 대수는 10000대 까지이므로

매번 차량마다 모든 차량을 확인하는 것은 최악의 경우 무려 1억이므로 선형시간에 해결해야 함을 알고 있었다.

몇 시간동안 문제를 보면서 규칙을 알아냈다.

진출 지점을 기준으로 정렬을 하면, 

가장 값이 적은 진출 지점 이전의 진입 지점들의 차들을 카메라 하나로 모두 만나게 할 수 있다.

아래의 코드는 이러한 특징을 이용한 코드이다.

<hr>


### 🔑 코드

```python
def solution(routes):
    answer = 0
    routes.sort(key= lambda x : x[1])
    minE = routes[0][1]

    for r in routes:
        if r[0] > minE:
            answer += 1
            minE = r[1]

    return answer + 1
```

차량들을 진출 지점을 기준으로 정렬하고,

처음 현재 진출 지점을 가장 작은 진출 지점으로 잡는다.

모든 차량을 순회하면서 진입 지점이 현재 진출 지점보다 큰 시점에서 카메라 하나를 설치하고

현재 진출 시점을 새로 바꿔준다.

이렇게 하면 마지막으로 진출한 지점을 세지 못하므로 +1을 해준다.

