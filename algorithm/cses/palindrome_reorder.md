---
layout: page
title: "/palindrome_reorder"
permalink: /palindrome_reorder
---

# palindrome_reorder

<img src="/assets/images/cses/palindrome_reorder.png" width="100%" alt="palindrome_reorder" />


```python
def solution(string):
    counter = {}
    for c in string:
        if c in counter:
            counter[c] += 1
        else:
            counter[c] = 1
    odd_cnt = 0
    mid = ""
    left = ""
    for k, v in counter.items():
        if v % 2 != 0:
            odd_cnt += 1
            mid = k * v
        else:
            left += k * (v // 2)
        if odd_cnt >= 2:
            return "NO SOLUTION"
    return left + mid + left[::-1]
```