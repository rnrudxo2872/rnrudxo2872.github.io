---
date: 2021-10-07
title: "javascript vs typescript"
categories:
  - 개인공부
  - Typescript
tags:
  - 객체지향
  - javascript
  - typescript
---

typescript는 javascript 기반의 언어이며,
javascript는 클라이언트 측 스크립트 언어이고,
typescript는 객체 지향 컴파일 언어이다. 하지만 일반 컴파일 언어(C, C++...) 같은 언어의 컴파일 과정과는 다르기에(기계어로 바꾸는 컴파일러들과는 달리 javascript로 변환시키기에), <code>transpile</code>이라는 용어를 사용한다. 또는 meta programming이라고 한다.

- 스크립트 언어란? -소스 코드를 컴파일하지 않고 인터프리터를 통해 소스 코드를 한줄씩 바로 실행하는 방식으로 동작한다.
  - 컴파일을 하지 않고 바로 실행한다는 특징이 있지만, 소스코드를 읽으며 실행하기에 실행 속도는 컴파일러를 통한 언어보다 상당히 느리다.

---

## javascript

HTML 및 웹 개발에 가장 많이 사용되는 언어로, 실행을 위한 별도의 준비나 컴파일이 필요하지 않다.

- 특징
  1. 서버 커뮤니케이션
  - 페이지를 서버에 전송하기 전, 사용자 입력의 유효성을 검사하는 옵션 제공.
  1. 상호작용
  - 이벤트 및 애니메이션 생성 수행
  1. 멀티 스레딩, 멀티 프로세싱 기능이 없음.
  1. 낮은 reloading 속도

---

## typescript

오픈 소스기반 <code>객체 지향 프로그래밍 언어</code>이다. javascript superset이다.

- 특징
  1. 특정 가상 머신이나 런타임 환경 필요하지 않음.
  1. Transpiler
  - 오류 검사를 제공한다.
  - 개발자는 스크립트 실행전 오류를 잘 잡아낼 수 있다.
  1. Type checking
  - 정적 타입 검사(실행전) 기능 제공
  - 타입을 고정 시켜 주기에 개발자가 프로그래밍 시, 실행전 타입에 대한 오류를 찾기 쉽다.
