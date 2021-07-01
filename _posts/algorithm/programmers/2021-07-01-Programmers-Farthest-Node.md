---
date: 2021-07-01
title: "가장 긴 바이토닉 부분수열"
categories:
  - 알고리즘
  - 프로그래머스
tags:
  - algorithm
  - 프로그래머스
  - BFS
---

---

[문제](https://programmers.co.kr/learn/courses/30/lessons/49189?language=javascript)

---

## 구현

edge의 연결관계를 어떻게 구현할까 고민하다, 배열 인덱스에 관련된 노드들을 넣어두는 방식을 생각했다. Javascript에서는 배열 초기화를 어떻게 하나 알아보다가 Array.from이라는 것이 있다는 걸 알아 좋은 시간이였다.  
Queue를 기반으로 BFS로 root 노드인 1로부터 가장 먼 길이의 노드들의 개수를 얻어냈다.

```javascript
let answer = 0;
let maxLen = 0;
let conn;
let visit;

const bfs = (start) => {
  const Q = [];
  Q.push(start);
  visit[start.num] = true;

  while (Q.length > 0) {
    const curNode = Q.shift();
    const curNum = curNode.num;
    const curLen = curNode.len;

    if (maxLen === curLen) {
      answer++;
    }

    if (maxLen < curLen) {
      answer = 1;
      maxLen = curLen;
    }

    for (var i = 0; i < conn[curNum].length; ++i) {
      let nNum = conn[curNum][i];

      if (visit[nNum]) continue;

      Q.push({ num: nNum, len: curLen + 1 });
      visit[nNum] = true;
    }
  }
};

function solution(n, edge) {
  conn = Array.from({ length: n + 1 }, () => []);
  visit = Array.from({ length: n + 1 }, () => false);

  for (var i = 0; i < edge.length; ++i) {
    const A = edge[i][0];
    const B = edge[i][1];

    conn[A].push(B);
    conn[B].push(A);
  }

  bfs({ num: 1, len: 0 });

  return answer;
}
```
