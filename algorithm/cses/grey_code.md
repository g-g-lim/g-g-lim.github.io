---
layout: page
title: "/grey_code"
permalink: /grey_code
---

# grey_code

<img src="/assets/images/cses/grey_code.png" width="100%" alt="grey_code" />

```python
def solution(n):
    for i in range(2**n):
        print(bin(i ^ i >> 1)[2:].zfill(n))
```