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

## 등록

빈을 등록하려면 앞서 말한 것과 같이 root-context에 직접 입력하거나, @Component, @Bean(외부 라이브러리 객체화)으로 코드상 등록가능하다.

```java
//기본 singleton scope bean
@Component
public class BeanTest{
  ...
}

//prototype scope bean
@Scope('prototype')
@Component
public class BeanTest2{
  ...
}

@Scope('prototype')
@Bean
public class BeanTest3{
  ...
}
```

<br>

## Bean Scope 종류

- singleton
- prototype
- web
- - request
- - session
- - application
