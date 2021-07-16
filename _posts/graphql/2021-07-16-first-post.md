---
date: 2021-07-16
title: "GraphQL이란"
categories:
  - GraphQL
tags:
  - GraphQL
---

## GraphQL이란?

![graphql_logo](https://rnrudxo2872.github.io/assets/images/graphql/graphql_logo.png)

GraphQL은 페이스북에서 만든 쿼리기반의 언어이다. 한번 접해본 개발자들에게 인기가 좋은편이라고 한다.

---

## 왜 사용할까?

REST API에서 발생하는 over-fetching, under-fetching을 방지할 수 있으며, 쿼리문이 직관적이라 가독성도 좋다. 거기다 특정 DB, 플랫폼에 종속적이지 않으므로 여러모로 매력이 큰 친구다.
![rest_vs_graphql](https://rnrudxo2872.github.io/assets/images/graphql/rest_api_vs_graphql_api.png)
<sub>출처:https://www.apollographql.com/blog/graphql/basics/graphql-vs-rest/</sub>
<br>

---

## 구성방식

정의된 스키마를 호출(쿼리문 작성) 및 반환(resolver)을 하는 방식으로 진행된다.  
쿼리문 작성시, 2가지를 알 수 있는데, 쿼리와 뮤테이션(Mutation) 있다는 걸 알 수 있다.  
쿼리는 데이터를 불러오는(읽는:R) 목적으로 작성이 된다면, 뮤테이션은 단어의 의미에 맞게 데이터를 변조하는데 사용이 될 수 있다. CUD에 사용되며 함수라 생각하면 쉽게 이해가 되었다.
![graphql_query](https://rnrudxo2872.github.io/assets/images/graphql/graphql_query.png)  
![graphql_query](https://rnrudxo2872.github.io/assets/images/graphql/graphql_mutation.png)
