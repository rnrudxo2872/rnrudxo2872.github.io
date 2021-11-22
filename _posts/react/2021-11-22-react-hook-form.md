---
date: 2021-11-22
title: "React Hook Form 사용해 보기"
categories:
  - 개인공부
  - React
tags:
  - React
  - React-Hook-Form
  - typescript
---

## React에서의 Form 인증

순수 React로 form을 인증하는 방법으로는 각각 input의 값을 state로 관리하고, 제출할 때 인증절차를 해야한다. 하지만 각각의 state를 분배해줘야 하기에, 코드량이 상당히 많아진다.

<br><br>

```js
import { FormEvent, useState } from "react";

function App() {
  const [str, setStr] = useState("");
  const [iError, setIError] = useState("");

  const changeStr = (event: FormEvent<HTMLInputElement>) => {
    const {
      currentTarget: { value },
    } = event;
    setStr(value);
    setIError("");
  };
  const submitHandler = (event: FormEvent<HTMLFormElement>) => {
    event.preventDefault();

    if (str.length < 5) return setIError("너무 짧습니다!");
    console.log(`${str} 값이 제출 되었습니다.`);
  };

  return (
    <div className="App">
      <form onSubmit={submitHandler}>
        <input type="text" onChange={changeStr} value={str}></input>
        <br />
        {iError !== "" ? iError : null}
      </form>
    </div>
  );
}

export default App;
```

<br>

위의 코드는 input에 입력한 글자수를 5자 이상으로 제한하는 form 부분을 작성한 코드단이다. 해당 구현부를 본다면, 어떤이는 적당한 것 아니냐. 라고 말할 수도 있으나, 회원가입이나, 많은 정보를 요구하는 페이지라면 input 태그가 많아질 것이다. 위에서는 submitHandler의 if문의 추가와, changeStr과 같은 각각의 input에 들어가는 state를 관리하는 함수가 매우 늘어나게 되는 것이다.

<br>

## React-Hook-Form 사용

앞서 본 문제를 해결하기위해 React-Hook_Form을 사용한다. 해당 라이브러리를 사용한다면, 각각의 input에 여러 타입의 error를 지정할 수 있고, message도 간단히 발생시킬 수 있다. 그리고 가장 중요한 validation을 쉽게 구현할 수 있다.

<br><br>

```js
import { FormEvent } from "react";
import { useForm } from "react-hook-form"

interface IFormType {
  str: string;
}

function App() {
  const { register, handleSubmit, watch, formState:{errors} } = useForm<IFormType>();

  const onSubmit = (data:IFormType) => {
    console.log(data);
  }

  return (
    <div className="App">
      <form onSubmit={handleSubmit(onSubmit)}>
        <input type="text" {...register("str",{
          onChange:(event:FormEvent<HTMLInputElement>) => console.log(event.currentTarget.value),
          minLength:{
            value:3,
            message:"너무 짧습니다!"
          },
          required:{
            value:true,
            message:"너무 짧습니다!"
          }
          })}></input>
        {errors?.str?.message ? <span>{errors?.str?.message}</span> : false}
      </form>
    </div>
  );
```

<br>

첫번째 구현코드에서 react-hook-form을 사용하여 위와 같이 구현하였다. 이전과 달리 error에 대한 state를 따로 생성하지 않고, useForm에 있는 하나의 오브젝트에 추가 되어 쉽게 조회하여 프로젝트를 진행할 수 있다. 또한 여러 인증절차를 제공하며, validate에 커스텀 인증 함수를 적용할 수도 있다.
