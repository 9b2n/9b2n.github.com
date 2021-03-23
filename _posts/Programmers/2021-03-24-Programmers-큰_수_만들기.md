---
title: "Programmers : 큰 수 만들기"
date: 2021-03-24 02:57:00 -0400
categories: CodingTest
---



### 🔒 [Programmers : 큰 수 만들기](https://programmers.co.kr/learn/courses/30/lessons/42883)

<hr>


그리디 알고리즘을 이용하지 않고 이중 반복문으로 풀려다가 시간 초과로 인해 하루종일 고민했던 문제였다.

한참을 고민하다 이 문제가 왜 그리디 알고리즘일까? 를 생각하다가 해법을 알아냈다.

~~(문제를 보고 그리디 알고리즘으로 풀어야겠다고 생각을 해야하는데 거꾸로 접근해서 좀 아쉽다ㅠㅠ)~~

리스트를 순회하면서 지나친 수 보다 큰 수를 고르면 되기 때문이었다.

무슨 소리인지 코드를 보면 이해가 쉬울 것이다.

그리디에 한 발짝 다가간 것 같아서 살짝 뿌듯했다😊


<hr>


### 🔑 코드

```python
def solution(number, k):
    stack = []
    cnt = 0
    for i in number:
        while stack and stack[-1] < i and cnt < k:
            stack.pop()
            cnt += 1
        stack.append(i)
    while cnt < k:
        stack.pop()
        cnt += 1
    string = ''.join(stack)
    return string
```

이 문제를 선형시간으로 푸려면 스택이 하나 필요하다.

스택에는 순회한 숫자를 담는다.

스택이 빈 스택이 아니라면,

새로운 숫자가 들어오면 자신보다 큰 수가 나올때까지,

스택에 있는 수를 k개까지 제거하면 된다.

만약 리스트의 끝까지 순회했는데 k개를 모두 제거하지 못했다면,

남은 수만큼 뒤에서 제거해주면 된다.

풀고 나서보니 그렇게 어려운 문제는 아니었지만,

초보에게는 스택을 이용해야겠다는 생각이 잘 나지 않을 것이다.~~(내가 그랬다)~~