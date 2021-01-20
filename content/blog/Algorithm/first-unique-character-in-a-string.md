---
title: LeetCode | easy | 387. First Unique Character in a String
date: 2021-01-21 00:01:49
category: algorithm
thumbnail: { thumbnailSrc }
draft: false
---

> 문제 설명

Given a string, find the first non-repeating character in it and return its index. If it doesn't exist, return -1.

<br>

> 예시

```
s = "leetcode"
return 0.

s = "loveleetcode"
return 2.
```

<br>

---

<br>

> 풀이

```js
var firstUniqChar = function(s) {
  for (let i = 0; i < s.length; i++) {
    if (s.indexOf(s[i]) === s.lastIndexOf(s[i])) {
      return i
    }
  }
  return -1
}
```

> 다른 풀이

```js
var firstUniqChar = function(s) {
  for (let i = 0; i < s.length; i++) {
    const prev = s.indexOf(s[i], 0)
    const next = s.indexOf(s[i], i + 1)
    // indexOf()의 반환값이 -1이면 지정된 요소가 없는 경우입니다.
    if (prev === i && next === -1) {
      return i
    }
  }
  return -1
}
```

> What I learned

- lastIndexOf()

indexOf() 메서드와 마찬가지로 `문자열`과 `배열`에 공통적으로 쓸 수 있는 메서드입니다.
<br>마지막 요소를 찾는 법에는 `array[array.length — 1]` 와 `array.slice(-1)[0]` 등이 있습니다.

- indexOf()의 두 번째 인자

두 번째 인자로 시작할 index를 지정할 수 있습니다.
