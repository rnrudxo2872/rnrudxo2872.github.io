---
date: 2021-07-22
title: "Spring Bean이란?"
categories:
  - 개인공부
  - spring
tags:
  - spring
  - 개념
  - Bean
  - IoC
---

![spring_logo](https://rnrudxo2872.github.io/assets/images/spring/spring_logo.png)

## 빈(Bean)

Spring에서 IoC Container가 관리하는 자바 객체를 빈(Bean)이라고 한다.
new 연산자로 객체를 생성했다면, 이것은 빈이라고 칭할 수 없다.
Spring legacy 프로젝트에서는 root-context.xml에 스프링이 관리해야하는 bean을 설정한다.
