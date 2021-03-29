---
title: "Programmers : 구명보트"
date: 2021-03-29 22:32:00 -0400
categories: CodingTest
---



### 🔒 [Programmers : 구명보트](https://programmers.co.kr/learn/courses/30/lessons/42885)

<hr>

한 배에 최대 2명까지 탈 수 있다는 조건을 못 봐서 삽질을 많이 했다.

문제를 꼼꼼히 보는 습관을 들여야 할 것 같다.

처음엔 단순히 큰 순서나 작은 순서로 배에 태워봤지만 풀리지 않았다.

그래서 남아있는 사람들 중 제일 큰 무게와 제일 작은 무게를 같이 태워보다가 해결책을 찾았다.



<hr>


### 🔑 코드

```python
def solution(people, limit):
    answer = 0
    people.sort(reverse = True)
    l, r = 0, len(people)-1
    while l <= r:
        if limit >= people[l] + people[r]:
            l += 1
            r -= 1
        else:
            l += 1
        answer += 1

    return answer
```

사람들을 무게가 많이 나가는 순으로 정렬한 뒤,

남아있는 사람들 중, 맨 앞 사람(**l**) 과 맨 뒷사람(**r**)의 무게 합을 보고, 제한 무게(**limit**) 이하이면 한 배에 태워 보낸다.

그렇지 않으면 맨 앞 사람만 보낸다.

이 과정을 사람이 남아있지 않을 때까지(**l<=r**) 반복한다.