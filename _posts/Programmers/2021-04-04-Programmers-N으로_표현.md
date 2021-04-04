---
title: "Programmers : N으로 표현"
date: 2021-04-04 22:33:00 -0400
categories: CodingTest
---



### 🔒 [Programmers : N으로 표현](https://programmers.co.kr/learn/courses/30/lessons/42895)

<hr>

이 전의 결과값들을 이용하여 새로운 결과를 도출해내는 동적 프로그래밍 기법을 이용하면 된다.

N을 m번 사용했을 때 나올 수 있는 결과값은 이전 결과값들을 사칙연산하여 도출해낼 수 있다.

N을 1번 썼을 때 = N

N을 2번 썻을 때 = (1번 썼을 때 + 1번 썼을 때) + NN

N을 3번 썼을 때 = (1 + 2) + NNN

N을 4번 썼을 때 = (1 + 3) + (2 + 2) + NNNN

...

N을 8번 썼을 떼 = (1 + 7) + (2 + 6) + (3 + 5) + (4 + 4) + NNNNNNNN

그외 -1

이를 토대로 코드를 짜면 아래와 같다.



<hr>


### 🔑 코드

```python
def solution(N, number):
    result = [{}]
    for i in range(1,9):
        r = {int(str(N)*i)}
        for j in range(1,i//2+1):
            for x in result[j]:
                for y in result[i-j]:
                    r.add(x+y)
                    r.add(max(x,y)-min(x,y))
                    r.add(x*y)
                    if x != 0 and y != 0:
                        r.add(x//y)
                        r.add(y//x)
        if number in r:
            return i
        result.append(r)
    return -1
```

핵심 : N을 i번 사용했을 때의 결과값들을 **N을 i번 이어붙인 수**와 함께 result 리스트의 i번째에 저장한다.

0번 사용했을 때는 결과가 없으므로 빈 set을 넣었다.

8번 이후 사용은 -1을 리턴해야하므로 8까지만 반복문을 돌린다.

**i번째의 결과값들**은 **이전 결과 집합들을 이용**하여 사칙연산을 통해 얻는다.

얻어진 결과값들 중에 **number**가 있다면 **i**번 사용한 것이 제일 적은 수이므로 **i**를 반환한다.

그것이 아니라면 **result**에 **i번째 얻은 결과값들**을 저장한다.