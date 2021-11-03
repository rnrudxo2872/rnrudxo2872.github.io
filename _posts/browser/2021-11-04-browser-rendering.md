---
date: 2021-11-04
title: "브라우저의 랜더링 과정"
categories:
  - browser
tags:
  - browser
  - browser-rendering
  - reflow
  - repaint
---

## 브라우저의 렌더링 원리

브라우저가 화면에 나타나는 요소를 렌더링 할 때, 웹킷(Webkit)이나 게코(Gecko) 등과 같은 렌더링 엔진을 사용한다. 렌더링 엔진이 HTML, CSS, Javascript로 렌더링할 때, CRP(Critical Rendering Path)라는 프로세스를 사용하며 다음 단계들로 이루어진다.
<br><br>

1. HTML 파싱 후, DOM(Document Object Model) 트리 구축
1. CSS 파싱 후, CSSOM(CSS Object Model)트리 구축
1. Javascript 실행
   - ❗ HTML 중간에 스크립트가 있다면 HTML 파싱이 중단된다.
1. DOM과 CSSOM을 조합하여 렌더트리(Render Tree) 구축
   - ❗ <code>display: none</code> 속성과 같이 화면에서 보이지도 않고 공간을 차지하지 않는 것은 렌더트리로 구축되지 않는다. 또한 레이아웃에 포함되지 않는다.
   - ❗ <code>visibility: hidden</code>는 요소를 보이지 않게 하는 것은 <code>display:none</code>과 같지만, 레이아웃에서 공간을 차지한다.
1. 뷰포트 기반으로 렌더트리의 각 노드가 가지는 정확한 위치와 크기 계산(Layout/Reflow 단계)
1. 계산한 위치/크기를 기반으로 화면에 그린다.(Paint 단계)

## CRP 진행

1. Parse HTML을 통해 HTML 파싱 후, DOM 트리 구축
1. Parse Stylesheet를 통해 CSS 파싱 후, CSSOM 트리 구축
1. Evaluate Script를 통해 Javascript 실행
1. 렌더트리 구축
1. Layout을 통해 뷰포트 기준으로 렌더트리 노드들의 각 크기/위치 계산
1. Paint를 통해 Layout에서 계산한 값들로 각 요소를 화면에 그린다.

## Reflow, Repaint

- Reflow
  - Layout이 영향을 받을 경우, RenderTree 수정부터 다시 시작
- Repaint

  - Layout의 영향이 없는 css의 속성값들이 변경될 때 발생
  - reflow가 발생하면 repaint는 따라서 발생한다.

- document.createDocumentFragment()로 한번에 DOM에 요소들을 추가하여 한번만 reflow하도록 최적화가 가능하다.

참고:

[https://github.com/baeharam/Must-Know-About-Frontend/blob/main/Notes/frontend/browser-rendering.md](https://github.com/baeharam/Must-Know-About-Frontend/blob/main/Notes/frontend/browser-rendering.md)

[https://junilhwang.github.io/TIL/Javascript/Design/Vanilla-JS-Virtual-DOM/#\_3-virtualdom-%E2%86%92-realdom](https://junilhwang.github.io/TIL/Javascript/Design/Vanilla-JS-Virtual-DOM/#_3-virtualdom-%E2%86%92-realdom)

virtualDOM-reflow: [https://it-eldorado.tistory.com/87](https://it-eldorado.tistory.com/87)

vanilaJS fragment로 최적화 메모제이션: [https://simuing.tistory.com/entry/javascript-DOM-reflow-%EC%8B%9C-%EC%9E%90%EC%9B%90-%EC%86%8C%EB%AA%A8-%EC%B5%9C%EC%86%8C%ED%99%94-%EB%B0%A9%EB%B2%95](https://simuing.tistory.com/entry/javascript-DOM-reflow-%EC%8B%9C-%EC%9E%90%EC%9B%90-%EC%86%8C%EB%AA%A8-%EC%B5%9C%EC%86%8C%ED%99%94-%EB%B0%A9%EB%B2%95)
