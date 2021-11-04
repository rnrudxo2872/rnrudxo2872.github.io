---
date: 2021-11-04
title: "vanillaJS와 React의 랜더링 차이"
categories:
  - 개인공부
  - React
tags:
  - React
  - javascript
  - DOM
  - rendering
---

![react-logo](https://rnrudxo2872.github.io/assets/images/react/react-logo.png)
<sub>출처:[https://reactjs.org/](https://reactjs.org/)</sub>

javascript만으로 인터렉티브한 웹 페이지를 만들 수는 있다. 하지만 해당 태그의 inner 값을 바꾸면 reflow가 일어나는 것을 볼 수 있다. react는 virtual DOM을 통해 이런 엘리먼트 자체가 다시 랜더링되는 것을 방지하는데, 어떻게 동작하는지 알아보자.

```html
<!DOCTYPE html>
<head>
</head>
<body>
    <span>Total clicks: <span id="sp">0</span></span>
    <button id="btn">Click me</button>
</body>
<script>
    const button = document.querySelector('#btn')
    const span = document.querySelector("#sp")
    let counter = 0;

    function handleClick() {
        counter++;
        span.innerText = counter
    }
    button.addEventListener("click", handleClick)
</script>
</html>
```

순수하게 javascript만으로 counter 값이 바뀌는 이벤트를 만들어 봤다. 버튼을 클릭할 때, 개발자 도구를 켜서 elements를 확인하면 해당 값과 sp 아이디를 가진 span 태그가 값이 리랜더링 되는 현상을 볼 수 있다.  
그렇다면 react는 어떤가?

<br><br>

```html
<!DOCTYPE html>
<head>
</head>
<body>
    <div id="root"></div>
</body>
<script src="https://unpkg.com/react@17.0.2/umd/react.production.min.js"></script>
<script src="https://unpkg.com/react-dom@17.0.2/umd/react-dom.production.min.js"></script>
<script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
<script type="text/babel">
    const root = document.querySelector("#root")
    let count = 0;

    const upBtnHandler = () => {
        count++;
        ReactDOM.render(<Container/>,root);
    }

    const Container = () => (
        <div>
            <span>up count : {count}</span>
            <button onClick={upBtnHandler}>Click me</button>
        </div>)

    ReactDOM.render(<Container/>, root);
</script>
</html>
```

간단히 라이브러리를 불러와 바로 react를 적용시켜 보았다. 다시 개발자 도구를 켜서 클릭시 elements의 동작을 지켜보면, 해당 count 값만 다시 랜더링 되는 것을 볼 수 있다.
