---
date: 2021-06-13
title: "nodejs로 jwt 로그인 구현"
categories:
  - 개인공부
tags:
  - webpack
  - nodejs
---

---

# Webpack이란?

![webpack-graph](https://rnrudxo2872.github.io/assets/images/webpack/webpack-logo.png)

Javascript Module을 비롯한 그에 관련 리소스들의 의존성 관계를 분석하여, 브라우저들이 이해할 수 있는 하나의 번들, 혹은 여러개의 번들들로 묶고 패킹하는 Module Bundler이다.

---

# 다른 빌드 도구와 차이점?

![webpack-graph](https://rnrudxo2872.github.io/assets/images/webpack/webpack-main.png)  
<sub>출처:https://webpack.js.org/</sub>  
 Webpack은 다른 Grunt나 Gulp와 같은 빌드 툴이 아니며, 프로젝트 전체를 한 단위로 분석한다. 해당 webpack의 config파일에서 지정한 메인 파일 또는 지정 파일로부터 시작해 Javascript의 require, ES6라면 import문을 통해 건너건너 의존성을 파악 후, 로더를 통해 번들로 묶은 Javascript Bundle을 생성한다.

---

# 어디에 있나?

![frontFrameworks](https://rnrudxo2872.github.io/assets/images/webpack/frameworks.png)  
react.js나 Vue.js, Svelte같은 많은 대형 framework들은 이미 Webpack이 내장되어 있다. 그리고 수많은 기업들이 사용한다.(구글도 사용하니 말다했다.)

---

# Nodejs에서 사용

front단을 react를 사용하면 필요없을 것이나, 어떤 방식으로 config가 구성되는지, 설정하는지 알아보도록 하자.  
먼저 npm으로 webpack, webpack-cli 모듈을 설치해 준다.

```bash
npm install --save-dev webpack webpack-cli
```

그 다음으로 해당 프로젝트의 root폴더 기준에서 webpack.config.js 파일을 생성해준다. 만약, 프로젝트를 babel로 개발 중이라면, 해당 Javascript파일에서는 지원되지 않으므로 주의하자.  
해당 config파일에 본인이 변환할 entry를 설정해준다.

```javascript
const path = require("path");

module.exports = {
  entry: {
    main: "./client/js/main.js",
  },
  mode: "development",
  watch: true,
  output: {
    filename: "js/[name].js",
    path: path.resolve(__dirname, "assets"),
    clean: true,
  },
  module: {
    rules: [
      {
        test: /\.js$/i,
        use: {
          loader: "babel-loader",
          options: {
            presets: [["@babel/preset-env", { targets: "defaults" }]],
          },
        },
      },
    ],
  },
};
```

개발자 모드로 설정하였으며, 지속적인 명령문을 실행하지 않기위해 watch를 true로 해주었으며, 변경시 모든 파일들을 clean후 packing한 파일들을 저장하도록 했다.  
위처럼 entry Javascript을 설정하되, 본인은 Modern Javascript로 개발을 하기위해 babel loader를 추가로 설치하고 설정해주었다.<sub>https://www.npmjs.com/package/babel-loader</sub>

```bash
npm i babel-loader
```

그 후, scss도 사용하기 위해 추가적으로 sass-loader, css-loader, MiniCssExtractPlugin을
추가로 설치 후, config에 설정해 주었다.

```javascript
const MiniCssExtractPlugin = require('mini-css-extract-plugin');
...중략

...
module:{
        rules:[
            ,
            {
                test:/\.scss$/i,
                use:[
                    MiniCssExtractPlugin.loader,"css-loader","sass-loader"
                ]
            }
        ]
}
...
```

MiniCssExtractPlugin대신 style loader를 사용하였으나, css파일들을 head에 주입시키는 대신, 따로 파일을 빼두기 위해 대체하였다.  
loader는 실행순서의 역순으로 코딩하여야 한다.  
간단히 loader들을 살펴보면, sass-loader는 scss파일을 css로 컴파일 시켜주며, 그 다음으로 css-loader가 해당 import 파일들을 처리한다. 마지막으로 MiniCssExtractPlugin이 받아 css Bundle을 생성한다.

---

<sub>front단 작업을할 때, nodemon을 사용하는 사람들은 계속 서버가 리스타트 되는데, 이걸로 자원낭비하기 싫다면 nodemon.json에서 해당 파일들을 무시하게 해주면 된다.</sub>
