---
title: 'React의 가상 DOM이 최초로 그려지는 시기'
date: 2021-01-20
category: 'react'
draft: false
---

# Virtual DOM 이란?

UI의 가상의 요소들을 메모리에 저장하고 ReactDOM과 같은 라이브러리에 의해 실제 DOM과 동기화하는 프로그래밍 개념입니다.

이 과정을 [재조정](https://ko.reactjs.org/docs/reconciliation.html#gatsby-focus-wrapper)이라고 합니다.

<br>

# 언제 Virtual DOM이 처음 그려지게 될까?

> index.html

React 프로젝트에서 실제 DOM을 구성하게 될 html 파일이 존재하게 됩니다.

<br>

```html
<div id="root"></div>
```

<br>

> index.js

이 부분에서 id가 root인 엘리먼트를 ReactDOM 라이브러리를 통해 렌더하게 됩니다.

```js
import React from 'react'
import ReactDOM from 'react-dom'
import App from './App'

ReactDOM.render(<App />, document.getElementById('root'))
```

> `ReactDOM.render(<App />, document.getElementById('root'));`

1. ReactDOM 라이브러리의 render 함수의 첫 번째 인자로는 `컴포넌트 엘리먼트`가 오게 되고, 두 번째 인자에는 `실제 DOM 노드`가 오게 됩니다.

2. App 컴포넌트를 호출한 순간 내부적으로 `엘리먼트 트리`를 얻게 되고, App 컴포넌트 내부의 엘리먼트 트리 자신의 루트 엘리먼트를 시작점으로, 차근차근 마주친 엘리먼트들의 type을 검사하게 됩니다.

3. 실제 DOM 노드에서는 루트 엘리먼트를 바로 호출하였기 때문에 바로 자식 엘리먼트들에 대하여 type 검사를 하게 됩니다.

4. 두 개의 인자에 대한 type 검사가 끝나면 최종적으로 하나의 엘리먼트 트리를 얻게 됩니다.

**이때 얻게 된 엘리먼트 트리가 `virtual DOM`이고 이 순간 최초의 virtual DOM이 그려지게 됩니다.**

만들어진 virtual DOM을 실제 DOM에 반영을 하게 되면 React에서의 최초의 렌더링이 이루어집니다.
