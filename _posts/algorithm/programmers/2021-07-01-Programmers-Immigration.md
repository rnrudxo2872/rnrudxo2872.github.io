---
date: 2021-07-01
title: "입국 심사"
categories:
  - 알고리즘
  - 프로그래머스
tags:
  - algorithm
  - 프로그래머스
  - 이분탐색
  - Binary search
---

---

[문제]()

---

## 실수

읽고 어떻게 풀어야할지 고민을 많이 했다... 그러다가 식으로 적어보고 이해한 다음, 막상 구현을 하니 생각보다 빠르게 풀어졌다.

---

## 구현

Javascript의 sort에 비교함수를 다시금 생각하는 시간이 되었다.  
compare(a,b)에서 음의 값은 a가, 양의 값은 b가 앞으로 정렬된다.(0은 정렬하지 않는다.)
기억해두자.  
걸릴 수 있는 최대시간을 right로 잡고 이분탐색으로 구현하였다. 탐색시 범위의 중간값(모든 사람이 심사가 끝난시간)을 지정하고,
각 심사관들이 검사할 수 있는 사람의 수를 모두 합해, 주어진 사람 수와 비교하는 과정을 거쳤다.

```javascript
let TIMES;
let N;

const cmp = (a, b) => {
  return a - b;
};

const getSum = (mid) => {
  let sum = 0;
  TIMES.forEach((value) => (sum += Math.floor(mid / value)));

  return sum;
};

const binarySearch = (left, right) => {
  let mid = 0;
  while (left < right) {
    mid = Math.floor((left + right) / 2);

    //각 심사관 검사 할 수 있는 사람 수 * 각 심사관 검사 시간 = 총 걸린 시간
    const sum = getSum(mid);

    if (sum >= N) {
      right = mid;
    } else {
      left = mid + 1;
    }
  }
  return right;
};

function solution(n, times) {
  //오름차순 정렬
  TIMES = times.sort(cmp);
  N = n;

  const left = 0,
    right = times[times.length - 1] * n;

  return binarySearch(left, right);
}
```
