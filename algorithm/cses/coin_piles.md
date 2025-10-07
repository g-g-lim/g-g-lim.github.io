---
layout: page
title: "/coin_piles"
permalink: /coin_piles
---

# coin_piles

<img src="/assets/images/cses/coin_piles.png" width="100%" alt="coin_piles" />

```python
def solution(arr):
    for a, b in arr:
        det = 3
        det_x = a * 2 - b
        x = det_x / det
        det_y = b * 2 - a
        y = det_y / det
        if x >= 0 and y >= 0 and x == int(x) and y == int(y):
            print("YES")
        else:
            print("NO")
```