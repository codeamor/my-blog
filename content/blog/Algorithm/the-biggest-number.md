---
title: Programmers | Lv.2 | 가장 큰 수
date: 2021-01-23 21:01:63
category: algorithm
thumbnail: { thumbnailSrc }
draft: false
---

> 문제 설명

0 또는 양의 정수가 주어졌을 때, 정수를 이어 붙여 만들 수 있는 가장 큰 수를 알아내 주세요.

예를 들어, 주어진 정수가 [6, 10, 2]라면 [6102, 6210, 1062, 1026, 2610, 2106]를 만들 수 있고, 이중 가장 큰 수는 6210입니다.

0 또는 양의 정수가 담긴 배열 numbers가 매개변수로 주어질 때, 순서를 재배치하여 만들 수 있는 가장 큰 수를 문자열로 바꾸어 return 하도록 solution 함수를 작성해주세요.

> 제한 사항

- numbers의 길이는 1 이상 100,000 이하입니다.
- numbers의 원소는 0 이상 1,000 이하입니다.
- 정답이 너무 클 수 있으니 문자열로 바꾸어 return 합니다.

<br>

![image](https://user-images.githubusercontent.com/65898889/105578615-dc8af700-5dc4-11eb-9a65-c2dff6dbbc4b.png)

<br>

> 풀이

```js
function solution(numbers) {
  let result = ''

  numbers = numbers.map(element => String(element))
  // 정렬 부분이 생각하기 어려웠습니다.
  // 문자열 그대로 합한 경우가 숫자끼리 더한 경우보다 큰 경우를 처음에 생각하지 못했습니다. 문자열로 매핑을 해주고 문자열로 합한 조건을 사용해야 합니다.
  numbers.sort((a, b) => {
    return a + b > b + a ? -1 : 1
  })

  console.log(numbers)

  numbers.map(element => (result += element))

  // 마지막 테스트 케이스
  // numbers에 0만 들어오는 경우도 있을텐데 처음에 문제를 제대로 읽지 않아서 헤맸습니다.
  if (Number(result) === 0) {
    result = '0'
  }
  return result
}
```

<br>

> 다른 사람의 풀이

```js
function solution(numbers) {
  var answer = numbers
    .map(v => v + '')
    .sort((a, b) => (b + a) * 1 - (a + b) * 1)
    .join('')

  return answer[0] === '0' ? '0' : answer
}
```

```js
function solution(numbers) {
  let answer = numbers.sort((a, b) => `${b}${a}` - `${a}${b}`).join('')
  return answer[0] === '0' ? '0' : answer
}
```

> what I learned

- 문자열 형변환 방법
- 문자열에 1을 곱해주면 int 형으로 변환
- 템플릿 리터럴 접근

<br>

![image](https://user-images.githubusercontent.com/65898889/105579184-4658d000-5dc8-11eb-8657-318c87b13ec3.png)

<br>

# Reference

[Programmers](https://programmers.co.kr/learn/courses/30/lessons/42746?language=javascript)
