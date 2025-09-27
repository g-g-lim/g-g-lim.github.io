---
layout: page
title: "/2xN타일링찾기"
permalink: /2xN타일링찾기
---

# 2xN타일링찾기

<img src="/assets/images/programmers/2xN타일링찾기.png" width="100%" alt="2xN타일링찾기" />

```javascript
function solution(n) {
    let arr = [1, 1];
    for (let i = 1; i < n; i++) {
        const temp = arr[1];
        arr[1] = (arr[0] + arr[1]) % 1000000007;
        arr[0] = temp;
    }
    return arr[1];
}
```

```javascript
function solution(n) {
    let arr = [];
    arr.push([1]);
    for (let i = 1; i < n; i++) {
        const newArr = [];
        for (const e of arr) {
            if (e[e.length - 1] === 1) {
                newArr.push([...e, 1]);
                newArr.push([...e.slice(0, e.length - 1), 2]);
            } else {
                newArr.push([...e, 1]);
            }
        }
        arr = newArr;
    }
    return arr;
}
```