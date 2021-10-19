---
date: 2021-10-19
title: "localStorage와 sessionStorage"
categories:
  - browser
tags:
  - browser
  - localStorage
  - sessionStorage
---

## Web Storage

<code>web storage</code>는 데이터를 서버가 아닌 클라이언트에 저장할 수 있도록 지원하는 기능이다.  
쿠키와 유사한 기능을 가졌지만, 쿠키는 4KB까지 밖에 저장공간을 가지지 못하는 반면 웹 스토리지는 약 5MB정도의 저장공간을 가질 수 있다는 부분에서 차이점을 볼 수 있다.  
또한 데이터의 구조는 key-value로 이루어져 있으며, 데이터는 문자열로만 저장, 반환 된다.  
Javascript에서는 API를 이용해 Web Storage에 접근할 수 있다.

- Web Storage를 사용하려면 브라우저의 사양을 확인해볼 필요가 있다.
- 같은 <code>origin</code>내에서만 액세스 가능하다.
  <br><br>
- ORIGIN이란
  - URL 체계(http,https)
  - 호스트(.com) 등의 도메인
  - 포트(8080, 80, ... 등)

위의 모든 항목이 동일해야 액세스가 가능하다.

## Local Storage란

<code>localStorage</code>는 데이터를 브라우저에 반영구적으로 저장하며, 브라우저를 종료 후 재시작해도 데이터가 남아있다. 또한 다른 창과 브라우저를 통해서도 접근이 가능하다.  
Javascript를 통해 localStorage에 <code>setItem()</code>, <code>getItem()</code> 데이터를 저장 및 조회를 할 수 있다.  
객체 or 배열로 사용하고 싶다면, JSON을 이용한다.

```js
localStorage.setItem("foo", JSON.stringify({ name: "foo", class: "A" }));
```

localStorage는 데이터가 남아있기에 삭제하며 적절하게 사용해야 한다.(<code>removeItem()</code>,<code>clear()</code>)

## Session Storage란

<code>sessionStorage</code>는 브라우저가 닫히면 데이터는 사라지며, 다른 화면과 공유가 불가능 하다. 간단한 페이지간에 정보 전달, 공유 등으로 사용할 수 있다.

## 쿠키와의 차이점

쿠키는 일반적으로 서버와 통신할 때 HTTP헤더에 포함되어 전송이 된다. 서버측에서도 설정할 수 있다. 즉, 서버와의 세션관리 등에 사용된다.  
반면에, 웹 스토리지는 서버와 관계없이 클라이언트(브라우저)에서만 데이터를 관리한다.  
<br><br>
쿠키 또한 Javascript로 조작할 수 있다. 그래서 보안 이슈를 막기위해서는 httponly 특성을 붙여 Javascript단의 조작을 막아, 제 3자의 Javascript 수정 또는 xss를 예방한다.
