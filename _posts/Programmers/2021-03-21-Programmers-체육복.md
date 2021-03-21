---
title: "Programmers : 체육복"
date: 2021-03-21 21:46:00 -0400
categories: CodingTest
---



### 🔒 [Programmers : 체육복](https://programmers.co.kr/learn/courses/30/lessons/42862)

<hr>


옛날에 풀려고 시도했을 때는 어려워서 풀기 꺼려했는데, 지금 다시보니 풀기 쉬운 문제였다.

**탐욕법(Greedy)**이라는 개념이 어렵게 다가와서 아직도 탐욕법으로 문제를 풀기 힘들어하지만,

부딛혀보는 중이다.


<hr>


### 🔑 코드

```python
def solution(n, lost, reserve):
    lost = set(lost)
    reserve = set(reserve)

    lost2 = lost - reserve
    reserve2 = reserve - lost

    for r in reserve2:
        if r-1 in lost2:
            lost2.remove(r-1)
        elif r+1 in lost2:
            lost2.remove(r+1)

    return n-len(lost2)
```

문제 조건 중, 체육복 여벌을 갖고 온 학생도 도난 당했을 수 있다고 했으니,

lost 배열에 있는 원소가 reserve 배열에 존재할 수 있다.

그러므로 **lost, reserve** 배열 둘 다 **set** 자료형으로 바꿔

차집합 연산을 한다. 차집합 연산을 하면 두 배열의 중복된 원소를 없앨 수 있다.

두 배열간 중복 원소를 지운 뒤, reserve 배열 원소 기준으로 **앞 번호와 뒷 번호**가 lost 배열 안에 존재하는 지 확인하여 제거한다.

전체 학생 수에서 lost에서 남은 수를 뺀다.