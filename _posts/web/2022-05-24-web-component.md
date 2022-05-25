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

여기서 웹 컴포넌트를 사용하면, 위의 단점들을 조금 완화 시킬 수 있습니다.

- 컴포넌트로 캡슐화가 되어 있기에 원하는 곳에 적용 시키면 됩니다.
- 조금 빠르다. (네이티브 엘리먼트로 동작)

<br>

# 어떻게 사용할까?

웹 컴포넌트에는 4개의 Specifications가 존재합니다. (해석을 어떻게 해야할지...)

- Custom Elements
- Shadow DOM
- ES Modules
- HTML Template

정리하자면, 사용자정의 요소를 만들 수 있고(Custom Elements), 각 컴포넌트 당 캡슐화를 시켜 외•내부에 영향을 주지 않으며(Shadow DOM), 모듈로 사용성이 높고(ES Modules), 페이지 로드에서는 로드가 안되나 이후 런타임에 인스턴스화할 수 있습니다.(HTML Template)

가장 기본인 Custom Element를 만들어 봅시다.

```js
class MyComponent extends HTMLElement {
  constructor() {
    super();
    ...
  }
}

customElements.define("custom-tag", MyComponent);
```

위와 같이 클래스를 선언한 후, customElements에 define으로 태그를 등록할 수 있습니다. 이후, html 파일에 &lt;custom-tag&gt;를 사용할 수 있는 것 입니다.

<br>

그리고 캡슐화와 연관된 Shadow DOM과 웹 컴포넌트의 SEO는 어떤지에 대해서도 이후 글을 게시할 수 있도록 하겠습니다.
