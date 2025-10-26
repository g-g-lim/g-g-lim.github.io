---
layout: page
title: "/restaurant_customer"
permalink: /restaurant_customer
---

# restaurant_customer

```python
# min heap

def solve(customers):
    customers.sort(key=lambda x: (x[0], x[1]))
    cnt = 0
    min_heap = []
    for c in customers:
        while min_heap:
            if min_heap[0][0] <= c[0]:
                heapq.heappop(min_heap)
            else:
                break
        heapq.heappush(min_heap, (c[1], c[0]))
        cnt = max(len(min_heap), cnt)
        
    print(cnt)
```

```python
# sweeping

def solve(n):
    events = []
    for _ in range(n):
        a, b = map(int, input().split())
        events.append((a, 1))
        events.append((b, -1))

    events.sort()

    count = 0
    high = 0
    for t, d in events:
        count += d
        high = max(high, count)

    print(high)
```