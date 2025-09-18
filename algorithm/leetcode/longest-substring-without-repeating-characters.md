---
layout: page
title: "/longest Substring Without Repeating Characters"
permalink: /longest-substring-without-repeating-characters
---

# Longest Substring Without Repeating Characters

<img src="/assets/images/longest-substring-without-repeating-characters.png" width="100%" alt="longest-substring-without-repeating-characters" />

```python
def lengthOfLongestSubstring(self, s: str) -> int:
    n = 0
    memo = {}
    answer = 0
    for i in range(len(s)):
        if answer > len(s) - i:
            break
        while n < len(s):
            char = s[n]
            if memo.get(char):
                break
            else:
                memo[char] = True
            n += 1
        answer = max(answer, n - i)
        del memo[s[i]]
    return answer
```