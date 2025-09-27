---
layout: page
title: "/permutations"
permalink: /permutations
---

# Permutations

<img src="/assets/images/cses/permutations.png" width="100%" alt="permutations" />

```python
n = int(input())

def solution(n):
    if n == 1:
        return 1
    if n < 4:
        return "NO SOLUTION"
    arr = [2, 4, 1, 3]
    for i in range(5, n + 1):
        if i - arr[-1] == 1:
            temp = []
            temp.append(arr.pop())
            temp.append(arr.pop())
            arr.append(i)
            arr.append(temp.pop())
            arr.append(temp.pop())
        else:
            arr.append(i)
    return " ".join(map(str, arr))

print(solution(n))
```

###### https://cses.fi/problemset/task/1070