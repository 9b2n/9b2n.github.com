---
title: "Programmers : 소수 찾기"
date: 2021-03-19 14:56:00 -0400
categories: CodingTest
---



### 🔒 [Programmers : 소수 찾기](https://programmers.co.kr/learn/courses/30/lessons/42839)

<hr>

순열과 조합 문제이다.

permutations를 활용하면 수비게 풀리는 문제이고, 소수를 찾는 로직이 필요하다.



<hr>


### 🔑 코드

```python
from itertools import permutations
import math
def isPrime(n):
    for i in range(2,int(math.sqrt(n))+1):
        if n%i == 0:
            return False
    return True

def solution(numbers):
    answer = set()
    for i in range(1,len(numbers)+1):
        for tup in permutations(numbers, i):
            strNum = ''.join(tup)
            num = int(strNum)
            if num > 1 and isPrime(num):
                answer.add(num)

    return len(answer)
```

1자리 수 순열, 2자리 수 순열, ... , **len(numbers)**자리 수 순열을 조합하여 소수의 갯수를 찾으면 된다.

첫 번째 반복문은 **i** 자리 수 순열얻는 것이고

두 번째 반복문은 얻은 순열에서 소수를 찾는 것이다.

answer을 set구조를 이용하여 소수 중복을 없애고 갯수를 return한다.