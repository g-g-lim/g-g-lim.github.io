---
layout: page
title: "/two_knights"
permalink: /two_knights
---

# two_knights

<img src="/assets/images/cses/two-knights.png" width="100%" alt="two_knights" />
<img src="/assets/images/cses/two-knights-1.png" width="100%" alt="two_knights" />
<img src="/assets/images/cses/two-knights-2.png" width="100%" alt="two_knights" />
<img src="/assets/images/cses/two-knights-3.png" width="100%" alt="two_knights" />
<img src="/assets/images/cses/two-knights-4.png" width="100%" alt="two_knights" />

```python
k = int(input())

def solution(k):
    answer = [0, 6, 28, 96]
    cnt = {2: 4, 3: 8, 4: 4, 6: 0, 8: 0}
    for i in range(5, k + 1):
        cnt[6] += 4
        cnt[4] += 4
        cnt[8] = (i - 4) ** 2
        board_cnt = i * i
        result = []
        for key, value in cnt.items():
            result.append(((board_cnt - key - 1) * value))
        answer.append(sum(result) // 2)
    for v in answer[:k]:
        print(v)
```