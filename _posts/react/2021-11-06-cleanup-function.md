---
date: 2021-11-06
title: "Closeup Function"
categories:
  - 개인공부
  - React
tags:
  - react
  - useEffect
  - lifecycle
  - closeup
---

## useEffect

useEffect를 사용하면 마운트 될 때, 특정 state의 상태가 변경될 때마다 로직을 수행시킬 수 있도록 구현할 수 있다.

## closeup function 이란

useEffect에 return 으로 반환되는 함수를 의미한다. 해당 로직은 언마운트될 때, 혹은 특정 값이 업데이트 되기 직전에, 실행하려는 함수를 구현하면 된다.

```js
//언마운트
useEffect(() => {
  return () => console.log("해당 컴포넌트가 언마운트.");
}, []);

//업데이트 전
useEffect(() => {
  return () => console.log("특정dep가 값이 변하기 전.");
}, [특정dep]);
```
