---
date: 2021-10-07
title: "스코프 체인이란"
categories:
  - 개인공부
  - javascript
tags:
  - javascript
  - scope
  - scope-chain
---

![js_logo](https://rnrudxo2872.github.io/assets/images/javascript/js_logo.png)

## 스코프 체인(scope-chain)이란?

- 내부 함수에서는 외부 함수의 데이터(변수, 객체)에 접근할 수 있다. 하지만, 반대로 외부 함수에서는 내부 함수에 접근할 수가 없다.  
  <br>
  스코프 체인이라는 개념은 전역변수와 지역변수의 관계에서 나온다.

```js
let foo = "hi";
function something() {
  function innerSomething() {
    console.log(foo);
  }
  innerSomething();
}
something();
```

위와 같은 예시로 innerSomething은 foo를 출력하기 위해서 foo를 찾는다.  
우선 자신의 스코프 -> something의 스코프 -> global 스코프 순으로 찾아서 해당하는 값을 찾을 때까지 스코프를 전환한다. 이것을 <code>스코프체인(scope-chain)</code>라 한다.
