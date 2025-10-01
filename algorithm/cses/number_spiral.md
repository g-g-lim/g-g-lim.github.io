---
layout: page
title: "/number_spiral"
permalink: /number_spiral
---

# number_spiral

<img src="/assets/images/cses/number_spiral.png" width="100%" alt="number_spiral" />


```python
n = int(input())
arr = [map(int, input().split(" ")) for i in range(n)]

def solution(idx_list):
    for x, y in idx_list:
        max_idx = max(x, y)
        diag = (max_idx, max_idx)
        diag_value = max_idx**2 - (max_idx - 1)
        if diag[0] == x and diag[1] == y:
            print(diag_value)
            continue

        if max_idx % 2 == 0:
            if diag[0] > x:
                print(diag_value - (diag[0] - x))
            else:
                print(diag_value + (diag[1] - y))
        else:
            if diag[0] > x:
                print(diag_value + (diag[0] - x))
            else:
                print(diag_value - (diag[1] - y))

solution(arr)
```

###### https://cses.fi/problemset/task/1071