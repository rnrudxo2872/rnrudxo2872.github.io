---
date: 2021-08-19
title: "var와 let,const 차이는?"
categories:
  - 개인공부
  - javascript
tags:
  - javascript
  - ES6
---

![js_logo](https://rnrudxo2872.github.io/assets/images/javascript/js_logo.png)

## var, let, const

var는 자바스크립트에 변수를 선언하게 해주는 예약어이다. ES6부터는 let과 const를 추가적으로 선언할 수 있다.

---

## var, let 차이

우선 const는 성질이 조금 다르니, 제외하고 var와 let의 차이점을 알아보겠다.

- <code>var</code>는 중복선언이 가능하다. 하지만 <code>let</code>은 중복선언이 불가능하다.
- <code>var</code>는 선언전에 사용가능하다(hoisting).g 하지만 할당은 호이스팅이 되지않기에, undefined가 찍힐 것이다. <code>let</code>과 <code>const</code>은 호이스팅이 되나, TDZ 때문에 할당하기 전에는 호이스팅이 불가능하다.

```js
let age = 30;
function showAge() {
  console.log(age);
  let age = 25;
}
```

호이스팅이 되지 않았다면, 위의 코드에서 age가 30으로 정상적으로 출력이 될 것이나, let도 호이스팅이 되기에 TDZ에 의해 에러가 발생한다.

둘의 차이를 제대로 볼 수 있는 것으로 <code>영역(scope)</code>의 차이와 <code>호이스팅(hoisting)</code>동작 차이다.

### 영역

var는 <code>함수 영역(function-scoped)</code>를 가지며, let과 const는 <code>블록 영역(block-scoped)</code>를 가진다.

### 호이스팅

호이스팅은 선언을 코드상 하단에 위치하는데, 상대적으로 상단에서 그 변수를 사용해도 가능하도록 하는 것이다. 즉 영역 내부 어디에서든 변수 선언은 최상위에 선언된 것처럼 행동하는 것이다.

```javascript
console.log(hi); //undefined
var hi = "Hi!";
```

```javascript
var hi;
console.log(hi);
hi = "Hi!";
```

즉, 위의 첫번째 코드는 두번째와 같이 동작한다.  
let은 위와 같이 작성한다면 <b>ReferenceError</b>가 발생한다. 이는 <code>TDZ(Temporal Dead Zone)</code>때문에 초기화 되기전에 액세스할 때 에러를 발생시키기 때문이다. TDZ는 코드를 예측가능하게 하고 잠재적인 버그를 줄일 수 있다는 장점이 있다.

---

## const

const는 c/c++을 알고있는 사람들에게는 익숙할 것이다. javascript에서도 똑같이 상수화한다고 생각하면 편하다. 즉, 영역 내에서 재선언이 불가하고, 데이터를 바꿀 수 없다.
const도 let과 같이 호이스팅시 TDZ에 영향을 받는다.

---

## 변수의 생성과정

변수의 생성과정은 <code>선언단계</code>, <code>초기화 단계</code>, <code>할당 단계</code>로 나눈다.

- var
  - 선언 및 초기화 단계(undefined)
  - 할당 단계
- let
  - 선언 단계(호이스팅)
  - 초기화 단계
  - 할당 단계
- const
  - 선언 + 초기화 + 할당 단계
