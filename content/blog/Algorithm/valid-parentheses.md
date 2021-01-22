---
title: LeetCode | easy | 20. Valid Parentheses
date: 2021-01-22 18:01:00
category: algorithm
thumbnail: { thumbnailSrc }
draft: false
---

> 문제 설명

Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

Open brackets must be closed by the same type of brackets.
Open brackets must be closed in the correct order.

> 예시

```js
Example 1:

Input: s = "()"
Output: true

Example 2:

Input: s = "()[]{}"
Output: true

Example 3:

Input: s = "(]"
Output: false

Example 4:

Input: s = "([)]"
Output: false

Example 5:

Input: s = "{[]}"
Output: true
```

---

<br>

> 풀이

```js
var isValid = function(s) {
  let map = {
    ')': '(',
    ']': '[',
    '}': '{',
  }

  let arr = []
  for (let i = 0; i < s.length; i++) {
    if (s[i] === '(' || s[i] === '[' || s[i] === '{') {
      arr.push(s[i])
    } else {
      if (arr[arr.length - 1] === map[s[i]]) {
        arr.pop()
      } else return false
    }
  }
  return arr.length === 0 ? true : false
}
```

<br>

> what I learned

- 예전에 풀었던 문제인데 객체 연습하기에 좋은 문제인 것 같습니다.
