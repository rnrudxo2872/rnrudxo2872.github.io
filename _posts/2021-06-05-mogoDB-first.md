---
date: 2021-06-05
title: "mongoDB 시작하기"
categories:
  - 개인공부
tags:
  - web
  - Nodejs
  - express
  - mongoDB
  - DB
  - NoSQL
---

# MongoDB란?

데이터 베이스이며, NoSQL(Not Only SQL) 형태이다.
<sup><sub>[NoSQL이란?](https://rnrudxo2872.github.io/개인공부/nosql/)</sub></sup>

Document-Oriented(문서지향)적인 데이터 베이스이므로, MySQL이나 Oracle같은 기반으로 작성되는 RDBMS(Relational Database Management System) 데이터 베이스와 비교할 수 있다.

RDBMS와는 달리 Schema나 JOIN이 존재하지 않다.
데이터 구조는 key-value 형식이다.
![SQLvsNoSQL](https://rnrudxo2872.github.io/assets/images/sql_vs_nosql.png)

# Mongoose

Mongoose는 MongoDB의 ODM(Object Document Mapping)이다.
MongoDB와 자바스크립트간, 연결 해주는 매개체라고 할 수 있다.
해당 **JSON**형태의 **Documnet**를 **자바 스크립트 객체**로 바꿔주는 역할을 한다.

# Mongoose 설치

작업 중인 nodejs 프로젝트에 mongoose를 설치해준다

```bash
npm i mongoose
```

그 후, Mongoose와 MongoDB의 서버를 연결 해준다.

```javascript
import mongoose from "mongoose";

mongoose.connect("mongodb://[서버주소]/[디비명]", {
  useNewUrlParser: true,
  useUnifiedTopology: true,
  useFindAndModify: false,
  useCreateIndex: true,
});
```

##### p.s DB에 입력하는 query를 질의어라고도 한다.
