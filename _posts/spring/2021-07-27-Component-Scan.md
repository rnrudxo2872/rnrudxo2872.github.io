---
date: 2021-07-27
title: "Component-Scan이란?"
categories:
  - 개인공부
  - spring
tags:
  - spring
  - 개념
  - Component-Scan
---

![spring_logo](https://rnrudxo2872.github.io/assets/images/spring/spring_logo.png)

## Component-Scan 이란?

- **대표적으로 @Component, @Bean 또는 stereotype(@Controller,@Service,@Repository)를 Bean으로 등록하기위해 찾기위한 과정(어노테이션)이다.**

## 사용(설정) 방법

두가지 방법이 있다. xml에 직접 설정하거나, Java 코드로 설정하거나.

- ### xml로 설정하기

```xml
<context:component-scan base-package="com.test.first com.test.second">
</context:component-scan>
```

위와 같이 스캔할 클래스 base-package를 설정함으로써 Bean을 등록할 수 있다. 여기서 <code>exclued-filter</code>,<code>include-filter</code>로 제외할 stereotype, 특정 객체를 제외하거나 포함할 수 있도록 구별할 수도 있다.

- ### Java로 설정하기

```java
@Configuration
@ComponentScan({"com.test.first","com.test.second"})
public class ApplicationConfig{...}
```

위와 같이 <code>@Configuration</code>으로 xml을 대체하는 파일임을 명시하며, <code>@ComponentScan</code>을 통해 <code>basePackages</code>를 설정해준다.

---

## 동작과정

만약 Java단이라면,

- ConfigurationClassParser가 Configuration 클래스를 찾는다.(파싱)  
  -> @Configuration 어노테이션 클래스를 찾는것.
- ComponentScan 설정을 파싱함.  
  base-package 경로 패키지들을 기준, ComponentScanAnnotationParser가 스캔하기 위한 설정을 파싱.
- base-package 바탕으로 모든 클래스를 로딩한다.
- ClassLoader가 로딩한 클래스들을 BeanDefinition으로 정의.
- BeanDefinition 토대로 Bean을 생성.

xml로 설정한다면,

- context.xml이 읽히며 context:component-scan이 진행.
- 위와 같은 방식으로 base-package 경로를 토대로 부르고, 읽히며, 빈을 생성한다.
