---
date: 2021-06-09
title: "Window에서 Redis 설치"
categories:
  - 개인공부
  - database
  - redis
tags:
  - web
  - Redis
  - DB
  - NoSQL
---

# Redis

![Redis-logo](https://rnrudxo2872.github.io/assets/images/redis/redis-logo.png)

[Redis](https://redis.io/)는 key-value 형식으로 데이터를 저장하는 저장소로, 오픈소스 NoSQL이며 In-Memory DataBase이다.  
인스턴스 메세지나 게임 관련, 다른 데이터 베이스들과는 달리 In-Memory, 즉 메모리단에서 데이터를 주고받음으로 하드디스크에 저장
하는 다른 데이터 베이스들보다 데이터 조작을 매우 빠르게 할 수 있다는 큰 장점이 있다. 하지만, 메모리단이므로 휘발성이며, 용량에
제한이 있다는 단점이 있다.
많은 요청과 응답이 필요한 구조에서 사용하기 좋다.

---

# Redis 설치

redis에서는 정식적으로 window를 지원하지 않으므로, 윈도우에서 설치할 수 있도록 릴리즈해주는 팀이 있다. [해당페이지](https://github.com/tporadowski/redis/releases)에 가서 설치를 해주도록 하자.
![redis-release](https://rnrudxo2872.github.io/assets/images/redis/redis-release.png)  
해당 5.0.9버전 msi 파일을 다운받아 설치하였다. 모든 설정은 Next로 기본 설정을 지킨채로 진행하였다.

---

# 확인

윈도우이므로 환경변수로 해당 설치경로로 해주었다. 그 후, `redis-cli`을 실행시키면,  
![redis-cli](https://rnrudxo2872.github.io/assets/images/redis/redis-cli.png)  
위와 같은 화면이 나올 것이다.  
![redis-cli-ping](https://rnrudxo2872.github.io/assets/images/redis/redis-cli-ping.png)  
ping을 하고 서버측에서 pong의 응답이 온다면 제대로 된 것이다.

<sub>ref: https://hwigyeom.ntils.com/entry/Windows-%EC%97%90-Redis-%EC%84%A4%EC%B9%98%ED%95%98%EA%B8%B0-1</sub>
