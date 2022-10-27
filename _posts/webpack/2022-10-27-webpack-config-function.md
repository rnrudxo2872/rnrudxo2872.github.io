---
date: 2022-10-27
title: Webpack 구성에서 개발 모드 구분 및 소스매핑 적용
categories:
- 개인공부
tags:
- webpack
- nodejs
- devtool
---

<br>

# 개요
회사에서 맡게된 작업물을 끝낸 후, 이전에 끝냈던 프로젝트를 다시 살펴보았습니다. 처음 맡게된 프로젝트였기에, 조심스러움과 존재하지 않은 제약을 신경쓰다가 놓친게 많았던 걸로 기억에 남아있었기 때문입니다.  
그 중 하나가 개발 환경이였습니다. 여러가지 문제가 있지만... development 모드일 때 소스가 보기 매우 어려웠습니다. Javascript에서 Typescript로 마이그레이션하는 작업이 있었는데, 여기서 소스 매핑이 필요한 것을 절실하게 느끼며, 작업했던 것을 기억하고자 글을 써보려 합니다.
<br><br>

# 문제점
버그가 일어난 라인에 가면 아래와 같은 화면을 볼 수 있었습니다.  
![before-mapping](https://rnrudxo2872.github.io/assets/images/webpack/before-source-mapping.png)

알아보지 못할 정도는 아니지만, 기존 소스와 많이 달라진 모습이였는데요. 문제의 라인은 복잡하지 않은 코드라 문제가 없을지도 모릅니다만, 이후에는 어떻게 될지 모르기에 수정이 필요하다고 생각 되었습니다.  
 <br><br>


# 수정

Webpack configuration에 devtool 옵션을 설정하면 해당 문제를 수정할 수 있습니다. [[참조]](https://webpack.js.org/configuration/devtool/#devtool)  
devtool 옵션의 값의 따라 rebuild 속도, 원본과의 차이(코드 라인 등)의 수준을 설정할 수 있습니다.

```js
// webpack.config.js
module.exports = {
    //...
    devtool: "eval-cheap-module-source-map"
}
```

문제가 되었던 코드의 화면은 아래와 같이 매핑됩니다.  
![after-mapping](https://rnrudxo2872.github.io/assets/images/webpack/after-source-mapping.png)  
조금 보기 쉽습니다.  

<br>

**Typescript 프로젝트**라면 tsconfig파일에 sourceMapping 옵션을 활성화 해줘야 합니다. [[참조]](https://www.typescriptlang.org/tsconfig#sourceMap)  

```js
{
  "compilerOptions": {
    "sourceMap": true,
    //...
  }
}
```

<br><br>

# 개발 모드 구분
소스 맵핑은 프로덕션에서는 불필요하니, 개발 모드에만 해당 설정이 되었으면 좋겠다고 자연스레 생각하게 되었습니다. 그래서 프로덕션 모드와 개발 모드를 구분해야할 수 있어야 하는데요.  
<br>
object에서 function exporting을 하도록 변경 후, 개발 모드에서만 소스 매핑을 하도록 설정합니다.  
```js
module.exports = (env, argv) => {
    const { mode } = argv;

    return {
        // ...webpack configuration object
        devtool: mode === "development" ? "eval-cheap-module-source-map" : false
    }
}
```
