---
layout: page
title: "/knight_moves_grid"
permalink: /knight_moves_grid
---

# knight_moves_grid

```python
def solution(n):
    grid = [[0] * n for _ in range(n)]

    dx = [1, 1, -1, -1, -2, 2, -2, 2]
    dy = [-2, 2, -2, 2, 1, 1, -1, -1]
    
    q = deque()
    q.append((0, 0))
    grid[0][0] = 1

    while q:
        x, y = q.popleft()
        for i in range(8):
            vx = x + dx[i]
            vy = y + dy[i]
            if vx < 0 or vy < 0 or vx >= n or vy >= n:
                continue
            if grid[vx][vy] != 0:
                continue
            grid[vx][vy] = grid[x][y] + 1
            q.append((vx, vy))

    print_board(grid)

def print_board(grid):
    out_lines = []
    for i in range(n):
        out_lines.append(" ".join(str(grid[i][j] - 1) for j in range(n)))
    sys.stdout.write("\n".join(out_lines))
```