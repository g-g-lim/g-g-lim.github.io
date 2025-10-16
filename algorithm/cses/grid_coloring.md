---
layout: page
title: "/grid_coloring"
permalink: /grid_coloring
---

# grid_coloring

```python
def solve(n, m, board):
    alphabets = ["A", "B", "C", "D"]
    path = [(-1, 0), (0, -1)]
    for i in range(n):
        for j in range(m):
            s = set()
            s.add(board[i][j])
            for d1, d2 in path:
                x = i + d1
                y = j + d2
                if x < 0 or y < 0 or x >= n or y >= m:
                    continue
                s.add(board[x][y])
            for a in alphabets:
                if a not in s:
                    board[i][j] = a
                    break
    for b in board:
        print("".join(b))

```