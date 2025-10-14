---
layout: page
title: "/max_grid_construction"
permalink: /max_grid_construction
---

# max_grid_construction

<img src="/assets/images/cses/max_grid_construction.png" width="100%" alt="max_grid_construction" />


```python
def solution(n):
    board = [[0] * n for _ in range(n)]
    column_sets = {}
    row_sets = {}
    for i in range(n):
        column_sets[i] = set()
        row_sets[i] = set()

    for i in range(n):
        for j in range(n):
            if i == j:
                column_sets[i].add(0)
                row_sets[j].add(0)
                continue
            r = board[i][j]
            if r != 0:
                continue

            c_set = column_sets[i]
            r_set = row_sets[j]
            s = 0
            while True:
                if s in c_set or s in r_set:
                    s += 1
                else:
                    board[i][j] = s
                    c_set.add(s)
                    r_set.add(s)
                    board[j][i] = s
                    column_sets[j].add(s)
                    row_sets[i].add(s)
                    break

    for c in board:
        print(*c)
```