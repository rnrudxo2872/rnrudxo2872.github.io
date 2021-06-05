---
date: 2021-06-05
title: "NoSQL"
categories:
  - 개인공부
tags:
  - server
  - stateless
  - stateful
---

# Stateful? Stateless?

해석 그대로에서 알 수 있듯, 존재 상태를 뜻한다.
서버로 의미를 들여온다면, **Client**의 정보를 **Server**가 가지고 있는 서비스이냐, 아니냐로 추상적으로 나눌 수 있다.

# 특성

- **Stateful** 서비스는 서버 확장성에 어려움이 있다. 즉 Scale out시, 그 서버에 Client 정보가 사라지는 것이다. 그래서 해당 클라이언트가 접속시, 인증이 불가하다.

- **Stateless** 서비스는 서버가 request를 받을 때마다, 외부 DB 혹은 데이터를 조회하여 해당 Client에게 Token을 부여한다. 그래서 Scaling에 자유롭다는 큰 이점과 서버에 부하를 덜어낸다는 특성이 있다.
