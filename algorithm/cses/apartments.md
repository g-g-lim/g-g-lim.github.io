---
layout: page
title: "/apartments"
permalink: /apartments
---

# apartments

<img src="/assets/images/cses/apartments.png" width="100%" alt="apartments" />


```python
def solve(ap, am, k):
    ap.sort()
    am.sort()

    ap_idx = 0
    am_idx = 0
    cnt = 0
    while ap_idx < len(ap) and am_idx < len(am):
        ap_value = ap[ap_idx]
        am_value = am[am_idx]
        if ap_value - k <= am_value <= ap_value + k:
            cnt += 1
            ap_idx += 1
            am_idx += 1
        elif ap_value > am_value:
            am_idx += 1
        else:
            ap_idx += 1
    print(cnt)
```