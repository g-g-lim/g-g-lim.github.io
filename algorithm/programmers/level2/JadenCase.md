---
layout: page
title: "/JadenCase"
permalink: /JadenCase
---

# JadenCase

<img src="/assets/images/programmers/JadenCase.png" width="100%" alt="JadenCase" />

```javascript
function solution(s) {
    let flag = false;
    return s.split('').map((c) => {
        if (c === ' ') {
            flag = false;
            return c;
        } else if (/^[A-Za-z]$/.test(c)) {
            if (!flag) {
                flag = true;
                return c.toUpperCase();
            } else {
                return c.toLowerCase();
            }
        } else {
            flag = true;
            return c;
        }
    }).join('')
}
```