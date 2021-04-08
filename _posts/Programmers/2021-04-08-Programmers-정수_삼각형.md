---
title: "Programmers : 정수 삼각형"
date: 2021-04-08 22:00:00 -0400
categories: CodingTest
---



### 🔒 [Programmers : 정수 삼각형](https://programmers.co.kr/learn/courses/30/lessons/43105)

<hr>

이 문제에서 요구하는 것은 거쳐간 숫자의 합이 가장 큰 경우, 즉 경로의 값들을 모두 더한 수 중 가장 큰 경우를 말한다.

DP문제를 풀 때 자주 접근하는 방법인데, 거꾸로 풀어보는 것이다.

이 문제로 예를 들면 문제에서 설명하는 방법대로 한다면,

현재 위치의 값들이 아래층 위치의 값들에 더해지면서 맨 아래까지 반복해야한다.

하지만 거꾸로한다면 아래 층의 값들을 위 층의 값들에 더하는 과정을 반복해서

꼭대기 층을 반환하면 된다.



<hr>


### 🔑 코드

```python
def solution(triangle):
    for i in range(len(triangle)-1,0,-1):
        for j in range(len(triangle[i-1])):
            triangle[i-1][j] += max(triangle[i][j],triangle[i][j+1])
    return triangle[0][0]
```

**triangle**의 제일 아래 층에서 순회를 시작한다.

위층 값의 인덱스를 **i**라고 한다면, **위층[i] = max(현재층[i], 현재층[i+1])**

이 된다.

이 과정을 반복하면 가장 위층이 문제에서 요구하는 모든 경로의 결과값 중 가장 큰 값이 된다.