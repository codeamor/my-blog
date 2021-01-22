---
title: LeetCode | easy | 53. Maximum Subarray
date: 2021-01-23 03:01:19
category: algorithm
thumbnail: { thumbnailSrc }
draft: false
---

> 문제 설명

Given an integer array nums, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.

> 예제

```
Example 1:

Input: nums = [-2,1,-3,4,-1,2,1,-5,4]
Output: 6
Explanation: [4,-1,2,1] has the largest sum = 6.

Example 2:

Input: nums = [1]
Output: 1

Example 3:

Input: nums = [0]
Output: 0

Example 4:

Input: nums = [-1]
Output: -1

Example 5:

Input: nums = [-100000]
Output: -100000
```

<br>

---

<br>

> 풀이

```js
var maxSubArray = function(nums) {
  // num 배열의 첫 번째 원소를 최대값으로 지정합니다.
  let max = nums[0]
  // 최대값을 현재 합계에 대입합니다.
  let curSum = max

  for (let i = 1; i < nums.length; i++) {
    // nums 배열의 원소가 num 배열의 원소와 현재 합계의 합보다 크면
    if (nums[i] > nums[i] + curSum) {
      // 현재 합계에 해당 nums 배열의 원소를 대입합니다.
      curSum = nums[i]
    } else {
      // 크지 않으면 해당 num 배열의 원소를 현재 합계에 더해갑니다.
      curSum += nums[i]
    }
    // 현재 합계와 최댓값 중에 큰 값을 최댓값에 대입합니다.
    max = Math.max(curSum, max)
  }
  return max
}
```

> 다른 사람의 풀이

```js
// 동적 프로그래밍
var maxSubArray = function(nums) {
  let max = nums[0]

  for (let i = 1; i < nums.length; i++) {
    nums[i] = Math.max(nums[i], nums[i] + nums[i - 1])
    max = Math.max(max, nums[i])
  }
  return max
}
```

> what I learned

- DP로 접근 가능한 줄 몰랐습니다. 배열의 부분 집합 배열을 찾아가는 것이니 이전에 풀었던 계단 오르기 문제와 비슷하게 트리 형식으로 분할하여 풀 수 있는 것 같습니다.
