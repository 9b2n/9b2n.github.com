---
title: "Programmers : 조이스틱"
date: 2021-03-21 21:54:00 -0400
categories: CodingTest
---



### 🔒 [Programmers : 조이스틱](https://programmers.co.kr/learn/courses/30/lessons/42860)

<hr>


어렵지 않고 재밌는 문제였다.

현재 위치에서 가까운 문자를 바꿔야하는 위치를 찾아가야한다.


<hr>


### 🔑 코드

```python
def where(idx, arr, name):
    left, right = -1, 1
    l = len(name)
    while -left < len(name) and name[idx + left] == arr[idx + left]:
        left -= 1
    while right < len(name) and name[(idx + right)%l] == arr[(idx + right)%l]:
        right += 1
    
    return left if -left < right else right

def solution(name):
    arr = list("A"*len(name))
    move, idx, cnt = 0, 0, 0
    for i in range(1, len(name[1:])):
        if arr[i] == i:
            cnt += 1
    while cnt < len(name):
        move += min(ord(name[idx])-ord(arr[idx]), ord('Z')-ord(name[idx])+1)
        arr[idx] = name[idx]
        cnt += 1
        mcnt = where(idx, arr, name)
        idx = (idx + mcnt) % len(name)
        move += abs(mcnt) % len(name)

    return move
```

**where**함수는 현재 위치에서 오른쪽과 왼쪽 중 **문자를 바꿔야하는 가까운 위치의 방향과 거리를 찾는 함수**이다.

반복문을 시작하기 전에 name에서 안 바꿔도 되는 문자의 개수를 cnt에 더해준다.

현재 위치의 문자를 바꿔주고 move를 올린 뒤 cnt를 1 늘린다.

옮겨야할 방향과 거리를 찾아 옮겨주고 옮긴 횟수만큼 move를 올려준다.

문자를 바꾼 수(**cnt**)가 글자수(**len(name)**)와 같아지면 종료한다.