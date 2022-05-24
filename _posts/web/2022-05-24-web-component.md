---
date: 2022-05-24
title: Web Component란?
categories:
  - 개인공부
  - web
tags:
  - web
  - web component
  - shadow dom
  - 캡슐
---

# 웹 컴포넌트가 뭐야?

> Web components are a set of web platform APIs that allow you to create new custom, reusable, encapsulated HTML tags to use in web pages and web apps.  
> <sub>출처:[https://www.webcomponents.org/introduction](https://www.webcomponents.org/introduction)</sub>

공식 사이트에서 설명하는 것처럼, 재사용, 캡슐화, 심지어 커스텀으로 HTML 태그를 만들어서 사용할 수 있는 웹 API라고 생각하시면 됩니다.

<br>

HTML 요소는 브라우저와 운영체제에 따라 뷰가 다르게 나오는 경우가 있습니다.  
![브라우저별_input-search](https://rnrudxo2872.github.io/assets/images/web/input-search_browser.png)  
<sub>[MDN 출처](https://developer.mozilla.org/en-US/docs/Learn/Forms/HTML5_input_types)</sub>

위와 같이 환경별로 제각각 표현되는 UI를 통일하게 보이도록 javascript로 컴포넌트를 생성하여 랜더링하게 되는데요.  
이런 환경에서 확대하고, HTML5에서 제공하는 기본 요소(element)만 사용하기에는 한계가 있습니다. 그래서 javascript를 이용한 컴포넌트를 생성하게 됩니다.

하지만 javascript 컴포넌트는 아래와 같은 단점이 존재합니다.

- 유연성이 낮다. (특정 HTML 구조, CSS, script 파일 별도로 요구)
- 느리다.
