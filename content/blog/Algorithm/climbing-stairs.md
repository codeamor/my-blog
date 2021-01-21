---
title: LeetCode | easy | 70. Climbing Stairs
date: 2021-01-22 00:01:69
category: algorithm
thumbnail: { thumbnailSrc }
draft: false
---

> 문제 설명

You are climbing a staircase. It takes n steps to reach the top.

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

> 예시

```
Input: n = 2
Output: 2
Explanation: There are two ways to climb to the top.
1. 1 step + 1 step
2. 2 steps
```

```
Input: n = 3
Output: 3
Explanation: There are three ways to climb to the top.
1. 1 step + 1 step + 1 step
2. 1 step + 2 steps
3. 2 steps + 1 step
```

> 제한 사항

```
1 <= n <= 45
```

<br>

---

<br>

> 다른 사람의 풀이

```js
// 동적 프로그래밍
let climbStairs = function(n) {
  let countingFunc = function(stairsRemaining, savedResults) {
    if (stairsRemaining < 0) {
      return 0
    }

    if (stairsRemaining === 0) {
      return 1
    }

    if (savedResults[stairsRemaining]) {
      return savedResults[stairsRemaining]
    }
    // 분할 정복, 트리 구조를 생각하면 편합니다.
    savedResults[stairsRemaining] =
      countingFunc(stairsRemaining - 1, savedResults) +
      countingFunc(stairsRemaining - 2, savedResults)

    return savedResults[stairsRemaining]
  }
  // 재귀 호출 시, 반복적으로 계산되는 것들의 계산 횟수를 줄이기 위해 이전에 계산했던 값을 저장해두고 나중에 재사용합니다.
  return countingFunc(n, {})
}
```

<br>

> what I learned

- 동적 프로그래밍 기초를 공부했습니다.
  개념만 읽었을 때는 감이 안왔는데 노드를 트리 구조화 시킨 설명을 보니 이해가 됐습니다.

- 동적 프로그래밍에서 쓰이는 분할 정복 기법과 메모이제이션을 공부했습니다.

<br>

# Reference

[Youtube](https://www.youtube.com/watch?v=UyDyc6yV1iQ) <br>
[Blog](https://www.zerocho.com/category/Algorithm/post/584b979a580277001862f182)
