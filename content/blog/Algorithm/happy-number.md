---
title: LeetCode | easy | 101. Happy Number
date: 2021-01-21 07:01:46
category: algorithm
thumbnail: { thumbnailSrc }
draft: false
---

> 문제 설명

Write an algorithm to determine if a number n is happy.

A happy number is a number defined by the following process:

- Starting with any positive integer, replace the number by the sum of the squares of its digits.
- Repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1.
- Those numbers for which this process ends in 1 are happy.

<br>

> 예시

```
Input: n = 19
Output: true
Explanation:
12 + 92 = 82
82 + 22 = 68
62 + 82 = 100
12 + 02 + 02 = 1
```

```
Input: n = 2
Output: false
```

<br>

> 풀이

```js
var isHappy = function(n, cnt = 0) {
  result = false
  // 문제에서 자릿수 제곱의 합의 값이 1이 될 때까지 끝없이 루프를 돌라고 말합니다.
  // 카운트 변수 최댓값 조건은 충분히 큰 숫자이면 될 것 같습니다.
  // 6 미만 조건부터 Submit할 시 Accepted가 떴습니다.
  if (cnt < 6) {
    let digitSum = n
      .toString()
      .split('')
      .reduce((acc, cur) => acc + cur * cur, 0)

    if (digitSum === 1) {
      return (result = true)
    }
    // 자릿수 제곱의 합이 1이 아니면 카운트를 증가시키고 재귀 함수를 실행합니다.
    else {
      cnt++
      isHappy(digitSum, cnt)
    }
  }
  return result
}
```

<br>

> 다른 풀이

```js
var isHappy = function(n) {
  // JS 내장 객체인 Set 객체
  const set = new Set()
  let result = 0

  // result가 1이 될 때 탈출합니다.
  while (result !== 1) {
    result = 0
    // n값이 0이 될 떄(n이 10보다 작으면) 탈출합니다.
    while (n !== 0) {
      result += (n % 10) ** 2
      n = Math.floor(n / 10)
    }

    // set 객체의 메서드를 이용하여 진위를 따지고 result를 추가시킵니다.
    if (set.has(result)) return false
    set.add(result)
    n = result
  }

  return true
}
```

<br>

> what I learned

- 첫 풀이에서 스코프 때문에 헷갈렸습니다.
  var, let, const 의 차이만 알고서 키워드를 사용하지 않아야 할 경우에 대해서는 잘 몰랐습니다. 스코프와 스코프 체인에 대해서 따로 정리해야 할 것 같습니다.

- JS 내장 객체 Set을 다시 공부하였습니다.
