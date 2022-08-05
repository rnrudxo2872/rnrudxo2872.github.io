---
date: 2022-07-21
title: 비동기 에러핸들링(JS)
categories:
  - 개인공부
  - javascript
  - 스터디
tags:
  - effective javascript
  - javascript
  - async
  - promise
---

javascript에서도 다른 언어들과 비슷하게 try...catch 문으로 에러핸들링이 가능합니다. 하지만 try 블럭 안에 비동기 동작이 존재하고, 해당 동작에서 에러가 발생할 때, 과연 동일하게 동작할 것인가? 라는 주제로 해당 글을 작성하려 합니다.

# async...await

나름 최신<code>async...await</code> 구문을 사용해서 try...catch...finally를 테스트 해 봅니다.

```js
function printStr(str) {
  return new Promise((resolve, reject) => {
    if (!str) {
      reject(new Error("옳지않은 인자값 입니다."));
      return;
    }
    resolve(console.log(str));
  });
}

async function asyncFunc() {
  try {
    await printStr("hi!");
    await printStr("");
    console.log("try end.");
  } catch (err) {
    console.error(err);
  } finally {
    console.log("finally.");
  }
}

asyncFunc();
```

try...catch...finally 문법을 그대로 사용해서 에러핸들링이 가능합니다.

그렇다면 <code>async...await</code>를 사용하지 않는다면, 비동기 동작에서 try...catch...finally가 정상적으로 동작할까요?

```js
function printStr(str) {
  return new Promise((resolve, reject) => {
    if (!str) {
      reject(new Error("옳지않은 인자값 입니다."));
      return;
    }
    resolve(console.log(str));
  });
}

function asyncFunc() {
  try {
    printStr("hi!");
    printStr(""); // Uncaught (in promise) Error
    console.log("try end.");
  } catch (err) {
    console.error(err);
  } finally {
    console.log("finally.");
  }
}
```

catch 블럭에서 해당 에러핸들링이 안되어 Uncaught Error가 출력됩니다.

# Promise

위에서 언급한 것과 같이, 단순하게 try...catch...finally를 사용하면 제대로된 동작이 안되는 것을 확인할 수 있는데요.  
해당 문제는 Promise의 메서드로 해결할 수 있습니다.

```js
function printStr(str) {
  return new Promise((resolve, reject) => {
    if (!str) {
      reject(new Error("옳지않은 인자값 입니다."));
      return;
    }
    resolve(console.log(str));
  });
}

function asyncFunc() {
  const onError = (err) => console.error(err);

  printStr("hi!")
    .then(() => {
      printStr("").then(() => console.log("try end."));
    })
    .catch(onError)
    .finally(() => console.log("finally"));
}

asyncFunc();
```

# callback

최근에 사용되는 <code>async...await</code>, <code>Promise</code>를 사용하지 않고, callback으로 비동기 에러핸들링을 간단하게 구현해 보았습니다.  
비동기 트리거로는 queueMicrotask를 사용했습니다.(setTimeout을 사용해도 됩니다.)

```js
function asyncGenerator(callback, predicate, onSuccess, onFailure) {
  queueMicrotask(() => {
    if (!predicate()) {
      onFailure();
      return;
    }
    onSuccess(callback());
  });
}

function printStr(str, onSuccess, onFailure) {
  asyncGenerator(
    () => (console.log(str), str),
    () => !!str,
    onSuccess,
    () => onFailure(new Error("옳지않은 인자값 입니다."))
  );
}

function throwErrorFinal(finalCallback, error) {
  try {
    throw error;
  } catch (err) {
    console.error(err);
  } finally {
    finalCallback();
  }
}

function asyncFunc() {
  const onError = throwErrorFinal.bind(null, () => console.log("finally."));
  printStr(
    "hi!",
    () => {
      printStr(
        "",
        () => {
          console.log("try end.");
        },
        onError
      );
    },
    onError
  );
}

asyncFunc();
```
