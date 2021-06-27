---
date: 2021-06-28
title: "nodeJs build 하기"
categories:
  - 개인공부
tags:
  - web
  - Nodejs
  - express
---

# build

이때까지 nodejs 프로젝트를 진행하면서 nodemon.json을 실행하는 스크립트 명령어로 개발해왔다. babel-node는 해당 개발 코드를 웹에 호환되도록 자바스크립트를 변환시켜 실행해주는데, 이대로 실제 서버에 올린다면 좋지 않을 것이다.  
그래서 코드를 압축하고 호환되는 코드로 바꾸는 과정 build를 해야한다.

---

# babel build

우선 babel cli 모듈을 설치해준다.

```bash
npm i --save-dev @babel/core @babel/cli
```

<br/>
그리고 script에 명령어를 추가한다.

```javascript
"script":{
    "build:server":"babel src -d build"
}
```

src 폴더에 모든 것을 빌드하여 build 폴더에 넣어두겠다는 명령어이다.  
그 후, build안에 프로젝트 서버를 시작하는 파일 (ex. index.js)를 node 명령어로 실행해 본다면 잘 작동할 것이다.  
만약, async/await 문법을 사용한다면 "regenerator-runtime/runtime.js"를 import 해주는걸 잊지말자.

```javascript
import "regenerator-runtime/runtime.js";
```

굳이 regenerator 모듈을 설치하기 싫다면, 깃허브에 있는 오픈소스를 import해도 된다.

---

# webpack 설정

프론트엔트단 프레임워크를 따로 다루지 않는다면, webpack의 config 파일을 조금 설정해야한다.
webpack.config에 mode를 써두었다면 그 대신에 script에 명령어를 사용해준다.

```javascript
"build:client" : "webpack --mode=production"
```

webpack이 bundle을 생성할 때, production으로 모드를 설정하는 명령어이다. production 모드는 코드를 웹상에서 호환성이 좋게 바꿔주는 것 포함, 압축시켜준다. 문법상 필요없는 line break나 공백을 모두 제거하고 압축하는 결과물을 보여준다.

---

# heroku deploy시 필요 명령어 정의

만약 프로젝트를 heroku에 deploy하고 싶다면, script에 start와 build 명령문을 정의해줘야 한다.  
본인은 webpack과 백엔드단을 동시에 빌드하도록 엮어주었다.

```javascript
 "scripts": {
    "start": "node build/index.js",
    "build": "npm run build:server && npm run build:client",
    ...
 }
```
