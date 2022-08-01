---
date: 2022-07-21
title: 비동기 동작에서의 에러핸들링(try...catch)
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

동시성 동작을 이해하며, 해당 동작에서 에러핸들링에 익숙해지기 위해 구문별로 <code>try...catch...finally</code> 와 동일한 동작을 하도록 구현합니다.

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
