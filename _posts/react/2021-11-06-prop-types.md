---
date: 2021-11-06
title: "React Prop Types"
categories:
  - 개인공부
  - React
tags:
  - react
  - react prop types
---

React로 프로젝트를 진행하다 보면, 프로젝트가 일정 수준 이상으로 커질 수가 있다.  
덩치가 커지는 만큼, 버그도 발생하기 쉬워지는데, 이러한 것을 방지하기 위해서, 보통 타입스크립트를 사용한다.  
<br>
하지만 자바스크립트의 유연함을 가지고 싶거나, 프로젝트 구현의 진행률이 크면, 타입스크립트로 변경하기 고민이 될 것이다.  
여기에 React Prop types 모듈을 사용하면, 컴포넌트가 받는 prop를 내장된 검사 기능들로 타입 검사를 할 수 있다.

## 설치

```bash
npm i prop-types
```

## 예시

```js
import PropTypes from "prop-types";

function Component({ title }) {
  return (
    <div>
      <h1>{title}</h1>
    </div>
  );
}

Component.propTypes = {
  title: PropTypes.string.isRequired,
};
```

<sub>참고: https://ko.reactjs.org/docs/typechecking-with-proptypes.html</sub>
