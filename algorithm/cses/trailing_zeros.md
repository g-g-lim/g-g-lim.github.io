---
layout: page
title: "/trailing_zeros"
permalink: /trailing_zeros
---

# trailing_zeros

<img src="/assets/images/cses/trailing_zeros.png" width="100%" alt="trailing_zeros" />


```python
def solution(n):
    cnt = 0
    while n > 0:
        div, _ = divmod(n, 5)
        cnt += div
        n = div
    print(cnt)
```