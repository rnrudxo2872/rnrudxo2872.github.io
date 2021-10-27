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
<br><br>
도메인 마다 별도로 localStorage가 생성된다.
<br><br>
windows 전역 객체의 LocalStorage라는 컬렉션을 통해 저장과 조회가 이루어 진다.
<br><br>
도메인만 같다면 전역으로 데이터를 공유 가능하다.
<br><br>  
Javascript를 통해 localStorage에 <code>setItem()</code>, <code>getItem()</code> 데이터를 저장 및 조회를 할 수 있다.  
객체 or 배열로 사용하고 싶다면, JSON을 이용한다.

```js
localStorage.setItem("foo", JSON.stringify({ name: "foo", class: "A" }));
```

localStorage는 데이터가 남아있기에 삭제하며 적절하게 사용해야 한다.(<code>removeItem()</code>,<code>clear()</code>)

## Session Storage란

<code>sessionStorage</code>는 브라우저가 닫히면 데이터는 사라지며, 다른 화면과 공유가 불가능 하다. 간단한 페이지간에 정보 전달, 공유 등으로 사용할 수 있다.
<br><br>
데이터가 지속적으로 보관되지 않으며, 현재 페이가 브라우징 되고 있는 브라우저 컨텍스트 내에서만 데이터가 유지된다.
<br><br>
windows 전역 객체의 <code>sessionStorage</code> 라는 컬렉션을 통해 저장과 조회가 이루어진다.
<br><br>
브라우저가 종료되면 SessionStorage가 삭제 된다.
<br><br>
LocalStorage와 같이 도메인별로 별도로 생성이 된다. 하지만 브라우저가 다르면 서로 다른 영역이므로 다른 브라우저는 데이터 공유가 불가능하다.(브라우저의 컨텍스트가 다름)

## 쿠키(Cookie)와의 차이점

- 쿠키란.
  - Cookie란 웹사이트에 의해 유저의 컴퓨터에 놓여지는 작은 텍스트 파일들이다. Cookie는 사이트에서 방문한 페이지를 저장하거나 유저의 로그인 정보를 저장하는 등 다양한 방법으로 사용된다. 그리고 문자열만 저장할 수 있다는 제한 있다.
    <br><br>
    쿠키는 일반적으로 서버와 통신할 때, 매번 HTTP헤더에 포함되어 전송이 된다. 서버측에서도 설정할 수 있다. 즉, 서버와의 세션관리 등에 사용된다.

> 왜 서버에 쿠키가 전송이 되는가? <br><br> 서버는 요청 자체만으로 그 요청이 누구에게서 오는지 알 수 없기 때문에 응답을 보낼 수가 없다. 이때 쿠키에 클라이언트에 대한 정보를 담아서 서버로 보내면 서버는 쿠키를 읽어서 내가 누군지 파악한다. 쿠키는 서버와 클라이언트 간의 지속적인 데이터 교환을 위해 만들어 졌기 때문에 서버로 계속 전송되는 것이다.

<br>
용량이 제한적이다. 하나의 사이트에서 저장할  수 있는 최대 쿠키수는 20개이며, 4KB로 제한되어 있다. 그러나 쿠키도 하위키를 이용하면 이러한 제한을 일부 해소할 수 있다. 대부분 쿠키의 제한까지 데이터를 저장하는 일은 드물다고 한다.
<br><br>
반 영구적으로 데이터를 저장이 가능하다. 쿠키는 만료일자를 지정하게 되어 있어 유효기간이 존재한다. 만료일자를 지정하지 않으면 <code>Session cookies</code> 가 된다. 만일 영구 쿠키를 원한다면 만료일자를 멀게 지정해야 한다.
<br><br>
- 쿠키 종류
  - Session Cookie: 보통 만료기간(expire date)을 설정하고 메모리에만 저장되며 브라우저 종료 시 쿠키를 삭제한다.
  - Persistent Cookie: 장기간 유지되는 쿠키파일로 저장되어 브라우저 종료와 관계없이 사용한다.
  - Secure Cookie: HTTPS에서만 사용하며, 쿠키 정보가 암호화되어 전송한다.
  - Third-Party Cookie: 방문한 도메인과 다른 도메인의 쿠키, 광고 배너 등을 관리할 때 유입 경로를 추적하기 위해 사용한다.

쿠키 또한 Javascript로 조작할 수 있다. 그래서 보안 이슈를 막기위해서는 httponly 특성을 붙여 Javascript단의 조작을 막아, 제 3자의 Javascript 수정 또는 xss를 예방한다.
<br><br>

- 쿠키 단점
  - 쿠키에 대한 정보를 매 헤더에 추가하여 보내기 때문에 상당한 트래픽을 발생시킨다.
  - 결제 정보 등을 쿠키에 저장하였을 때 쿠키가 유출되면 보안에 대한 문제점도 발생할 수 있다.

## 정리

- Web Storage는
  - 서버 전송이 없다.
    - 저장된 데이터가 클라이언트에 존재할 뿐 서버로 전송은 이루어 지지 않는다. 이는 네트워크 트래픽 비용을 줄여준다.
  - 단순 문자열을 넘어 객체정보를 저장할 수 있다.
    - 문자열 기반 데이터 이외의 체계적으로 구조화된 객체를 저장할 수 있는 점은 개발편의성을 제공해주는 주요한 장점이다. 단, 브라우저의 지원 여부를 확인해 봐야하는 항목이다.
  - 용량적인 제한이 덜 하다.
  - 영구 데이터 저장이 가능하다.
  - 만료 기간 설정이 없다. 즉, 적절하게 삭제 해줘야 한다.
  - 서버와 관계없이 클라이언트(브라우저)에서만 데이터를 관리한다.

#### 참고

[https://velog.io/@sjwngjs/JAVASCRIPT-%EC%9B%B9%EC%8A%A4%ED%86%A0%EB%A6%AC%EC%A7%80local-storagesessionstorage-%EB%9E%80](https://velog.io/@sjwngjs/JAVASCRIPT-%EC%9B%B9%EC%8A%A4%ED%86%A0%EB%A6%AC%EC%A7%80local-storagesessionstorage-%EB%9E%80)
