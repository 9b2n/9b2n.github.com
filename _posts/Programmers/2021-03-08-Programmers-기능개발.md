---
title: "Programmers : κΈ°λ₯κ°λ°"
date: 2021-03-08 22:16:00 -0400
categories: CodingTest
---

### π [Programmers : κΈ°λ₯κ°λ°](https://programmers.co.kr/learn/courses/30/lessons/42586)


progresses λ¦¬μ€νΈλ₯Ό μμμλΆν° μννλ©΄ λλ λ¬Έμ μ΄λ€.

μ§λμ¨μ΄ 100μ΄λ©΄ λμ΄λ―λ‘, progressesμ μμλ₯Ό νλμ© λ³Ό λλ§λ€ 100μμ λΊ κ°μ κ·Έ μμμ μ§νμλλ‘ λλλ©΄ λ©°μΉ (days)μ μμνλ μ§ μ μ μλ€.

μμμΌ λ§νΌ λ€μ κ°λ€λ μλ κ°(progresses[i]) + speeds[i]*days ν΄μ€λ€.

μ΄ μμμ λ¦¬μ€νΈμ μμ μ λ§νΌ λ°λ³΅νλ©΄ λμ΄λ€.



### π μ½λ

```python
from math import ceil
from collections import deque
def solution(progresses, speeds):
    answer = []
    progresses = deque(progresses)
    speeds = deque(speeds)
    cnt = 1

    while progresses:
        p = progresses.popleft()
        s = speeds.popleft()
        if p >= 100:
            cnt += 1
        else:
            answer.append(cnt)
            cnt = 1
            n = ceil((100-p)/s)
            for i in range(len(speeds)):
                progresses[i] += speeds[i]*n
    answer.append(cnt)

    return answer[1:]
```

μμμ ν΅μΌμ±μ μ£ΌκΈ° μν΄ μ²μ νμΈν  λλ answerμ κ°μ λ£μ΄μ£Όμκ³ , answerμ returnν  λλ μΈλ±μ€λ₯Ό 1λΆν° μμνμ¬ λ°ννλ€.