---
layout: page
title: "/string_reorder"
permalink: /string_reorder
---

# string_reorder

```python
def solve(string):
    cnt = {}
    cnt_sum = len(string)
    for c in string:
        if c not in cnt:
            cnt[c] = 1
        else:
            cnt[c] += 1

    def check(cnt_sum, cnt):
        _max = 0
        for c in cnt:
            if _max < cnt[c]:
                _max = cnt[c]
        return cnt_sum - _max + 2 <= _max

    sorted_cnt = dict(sorted(list(cnt.items()), key=lambda x: x[0]))
    reorder = ""

    while cnt_sum > 0:
        _sum = cnt_sum
        for c in sorted_cnt:
            if sorted_cnt[c] == 0 or (reorder and reorder[-1] == c):
                continue
            cnt_sum -= 1
            sorted_cnt[c] -= 1
            if not check(cnt_sum, sorted_cnt):
                reorder += c
                break
            cnt_sum += 1
            sorted_cnt[c] += 1
        if _sum == cnt_sum:
            return -1
    return reorder
```