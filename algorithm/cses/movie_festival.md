---
layout: page
title: "/movie_festival"
permalink: /movie_festival
---

# movie_festival

```python
n = int(input())

def solve(n):
    movies = []
    for _ in range(n):
        s, e = input().split(" ")
        movies.append((int(s), int(e)))
        
    movies.sort()
    
    watches = 1
    e = movies[0][1]
    for i in range(1, len(movies)):
        s, _e = movies[i]
        if e <= s:
            watches += 1
            e = _e
        else:
            e = min(_e, e)
    
    print(watches)
```