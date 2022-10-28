---
date: 2022-10-28
title: webpack devServer 적용기
categories:
- 개인공부
tags:
- webpack
- nodejs
- devserver
- hot-reload
- HMR
---

# 개요
[이전 포스팅](https://rnrudxo2872.github.io/%EA%B0%9C%EC%9D%B8%EA%B3%B5%EB%B6%80/webpack-config-function/)에서 개발환경에서 디버깅이 쉽도록, 소스매핑을 적용해 보았습니다.  
이번에는 개발할 때, development server를 띄워 즉각적인 피드백을 받기위해서 해당 설정을 webpack을 통해 적용시킨 과정을 정리하고자 합니다. 그리고 추가적으로 해당 **프로젝트에 어떤 문제**가 있었는지도 함께 정리하고자 합니다.

# 이전까지의 프로젝트 개발 환경
이전에는 webpack configuration에 따로 설정 없이 커맨드 라인에 watch와 개발 모드로 실행 후, [live server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer)을 실행시켰습니다. 작업하는데는 큰 이상이 없었지만 일일이 live server를 따로 켜야 하는게 번거로웠습니다. 하지만, CRA(Create React App)으로 리액트를 개발하면 live server에서 지원하는 hot-reload과 한 번의 명령어로 간편하게 환경을 실행시킬 수 있습니다. CRA도 webpack으로 구성되었으니, 같은 환경을 구성할 수 있습니다.

# devServer 추가
설정은 매우 쉽습니다.(문서 읽는 시간이 훨씬 오래 걸렸습니다...)  
webpack configuration 파일을 열어, 아래와 같은 옵션을 추가합니다. - webpack5 기준
```js
devServer: {
        // 포트 번호 설정
        port: 9000,
        // 핫 모듈 교체(HMR) 활성화 설정
        hot: true,
        // gzip 압축 활성화
        compress: true,
        static: {
          // 콘텐츠 제공 위치
          directory: path.join(__dirname, "src")
        }
      }
```

