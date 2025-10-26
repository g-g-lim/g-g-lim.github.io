---
layout: page
title: "/ferris_wheel"
permalink: /ferris_wheel
---

# ferris_wheel

<img src="/assets/images/cses/ferris_wheel.png" width="100%" alt="ferris_wheel" />

```python
def solve(weights, x):
    weights.sort()
    s, e = 0, len(weights) - 1
    cnt = 0
    while s <= e:
        if s == e or weights[s] + weights[e] <= x:
            s += 1
            e -= 1
        else:
            e -= 1
        cnt += 1

    print(cnt)
```