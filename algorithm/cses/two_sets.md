---
layout: page
title: "/two_sets"
permalink: /two_sets
---

# two_sets

<img src="/assets/images/cses/two_sets.png" width="100%" alt="two_sets" />


```python
def solution(n):
    s = sum(range(1, n + 1))
    group1 = []
    if s % 2 == 0:
        div = s // 2
        group1 = []
        group2 = []
        for i in range(n, 0, -1):
            if div >= i:
                group1.append(i)
                div -= i
            else:
                group2.append(i)

        print("YES")
        print(len(group1))
        print(" ".join(map(str, reversed(group1))))
        print(len(group2))
        print(" ".join(map(str, reversed(group2))))
    else:
        print("NO")
```