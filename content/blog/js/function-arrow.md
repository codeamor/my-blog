---
title: JS | 화살표 함수가 Function 키워드 함수를 완전히 대체할 수 없는 이유
date: 2021-01-21 20:01:65
category: js
thumbnail: { thumbnailSrc }
draft: false
---

# this 키워드의 동작 방식이 다르기 때문입니다.

> 기존 function 키워드 함수

```js
var friendship1 = {
  name: 'sumin',
  friends: ['jeongwon', 'jimin', 'yohan'],
  logFriends: function() {
    // 객체 리터럴에서의 this는 friendship1을 가리킵니다.
    // 따라서 변수 that도 friendship1을 가리키게 됩니다.
    var that = this;
    this.friends.forEach(function(friend) {
      console.log(that.name, friend);
    })
  }
}

friendship1.logFriends();
> sumin jeongwon
> sumin jimin
> sumin yohan
```

<br>

> 화살표 함수 적용

```js
const friendship2 = {
  name: 'sumin',
  friends: ['jeongwon', 'jimin', 'yohan'],
  logFriends() {
    // 여기서 화살표 함수의 역할은 logFriends 함수의 this를 forEach 함수의 this와 동일하게 만들어 주는 것입니다.
    // 따라서 따로 변수 that을 만들어 줄 필요가 없고, 바로 this 키워드(friendship2)의 키 값으로 name을 찾아갈 수 있습니다.
    this.friends.forEach(friend => {
      console.log(this.name, friend);
    });
  },
};

friendship2.logFriends();
> sumin jeongwon
> sumin jimin
> sumin yohan
```

<br>

> 결론

- 바깥 함수의 this를 그대로 쓰고 싶다면 화살표 함수를 사용할 수 있습니다.
- 그렇지 않다면 function 키워드 함수를 사용해야 합니다.
