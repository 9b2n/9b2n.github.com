---
title: "Programmers : 카펫"
date: 2021-03-19 15:23:00 -0400
categories: CodingTest
---



### 🔒 [Programmers : 카펫](https://programmers.co.kr/learn/courses/30/lessons/42842)

<hr>


이 문제는 완전 탐색보단 규칙을 찾는 로직이 핵심인 것 같아 보였다.


<hr>


### 🔑 코드

```python
def solution(brown, yellow):
    for row in range(1,yellow+1):
        if yellow % row == 0:
            col = yellow // row
            if brown == (row + 2) * 2 + (col * 2):
                return [col+2, row+2]
```

카펫의 **가로 길이 > 세로 길이**이기 때문에 세로 길이를 1부터 탐색했다.

노란색 전체 칸 수 = 노란색 가로 길이 * 노란색 세로 길이 이므로,

노란색 가로 길이 = 노란색 전체 칸 수 / 노란색 세로 길이 이다.

노란색을 갈색이 1칸씩 두르고 있으므로

갈색 칸 수 = (노란색의 세로 길이 + 2) * (2 + 노란섹 가로 길이 * 2)