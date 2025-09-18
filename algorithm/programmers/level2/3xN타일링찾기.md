---
layout: page
title: "/3xN타일링찾기"
permalink: /3xN타일링찾기
---

# 3xN타일링찾기

<img src="/assets/images/3xN타일링찾기.png" width="100%" alt="3xN타일링찾기" />

```javascript
function solution(n){
    if (n % 2 !== 0) {
        return 0;
    }
    if (n === 2) {
        return 3;
    }
    let dp = [0, 0, 3];
    for (let i = 2; i < n; i += 2) {
        let temp = dp[2];
        dp[2] = ((dp[2] * 3 + dp[1] * 2 + dp[0]) + 2) % 1000000007;
        dp[0] = (dp[1] * 2 + dp[0]) % 1000000007;
        dp[1] = temp;
    }
    return dp[dp.length - 1];
}
```