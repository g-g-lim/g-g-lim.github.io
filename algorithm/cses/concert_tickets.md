---
layout: page
title: "/concert_tickets"
permalink: /concert_tickets
---

# concert_tickets

- https://en.wikipedia.org/wiki/Disjoint-set_data_structure

```python
prices.sort()
roots = [idx for idx in range(n)]
res = []
 
for c in customers:
    if prices[0] > c:
        print(-1)
        continue
    l, r = 0, n
    while l < r - 1:
        m = (l + r) // 2
        if prices[m] > c:
            r = m
        else:
            l = m
    idx = l
    s = []
    while idx > -1 and roots[idx] != idx:
        s.append(idx)
        idx = roots[idx]
    if idx == -1:
        # res.append(-1)
        print(-1)
    else:
        print(prices[idx])
    root = max(idx - 1, -1)
    while s:
        node = s.pop()
        roots[node] = root
    roots[idx] = root
```