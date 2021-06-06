---
date: 2021-06-05
title: "Password Hash?"
categories:
  - 개인공부
tags:
  - web
  - password
  - Hash
---

# Hasing? Encryption?

해싱(Hashing)과 암호화(Encryption)는 일상에서 비슷한 의미로 통용된다. 하지만 암호학적으로 본다면 차이가 있는데, 가장 큰 차이는 '**방향성**'이다.
**해싱**은 단방향, 다시말해 다시 되돌리는 복호화가 불가능하다. 그리고 **암호화**는 양방향이며, 복호화가 가능하다는 차이가 있다.

---

# 평문(plain text)? 다이제스트(digest)?

평문(plain text)은 Client단에서 입력한 문자열 그대로를 의미한다. digest(hash value 또는 hash text)는 평문, 즉 Client가 입력한 Password를 Hash Function을 거쳐 나온 문자열 혹은 값을 의미한다.
![HashFunction](https://rnrudxo2872.github.io/assets/images/hash_Function.png)  
<sup><sub>출처: [https://www.thesslstore.com/blog/difference-encryption-hashing-salting/](https://www.thesslstore.com/blog/difference-encryption-hashing-salting/)</sub></sup>

## Hash Function의 종류

- SHA
- MD
- HAS
- WHIRPOOL

---

# 필요성?

만약 평문으로 Client의 정보를 DB나 다른 데이터 저장소에 저장한다면, 해당 저장소가 공격자(hacker)에게 노출되는 순간, 모든 Client의 정보가 노출되는 아주 위험한 경우가 발생한다.  
하지만, digest로 저장되어 있다면, 복호화가 불가능하기에 보안을 강화할 수 있는 것이다.

---

# Hashing으로 무조건 안전한가?

답은 No다. 공격자들에게는 많은 방법이 있으며, 그 중 해싱된 값들을 모아둔 rainbow table을 조회하거나, 애초에 Hash Function이 데이터의 빠른 검색을 위한 함수이다 보니, 무작위의 데이터를 계속해서 대입해 BruteForce로 값들을 추출할 수 있다.

---

# 대안

그렇다면, digest의 보안을 더 강화할 방법은 없을까? 아마 많은 방법이 있을 것이다. 그 중 2가지를 말하고자 한다.

### ◼ Key Stretching

말 그대로 해석하면 키를 늘린다? 라고 생각할 수 있다. 이의 원리는 Hash Function을 여러번 돌리는 것이다.  
예로 SHA-256을 사용한다고 가정할 때, 1234를 입력하면 digest는 아래와 같다.

```text
1번째
1234
 -> 03ac674216f3e15c761ee1a5e255f067953623c8b388b4459e13f978d7c846f4

2번째
03ac674216f3e15c761ee1a5e255f067953623c8b388b4459e13f978d7c846f4
 -> 756bc47cb5215dc3329ca7e1f7be33a2dad68990bb94b76d90aa07f4e44a233a

...
```

위와 같이 n번의 Function을 돌려 digest를 얻는다.  
Key Stretching을 한다면 물론 Client도 인증을 할 때, 시간이 더 걸리지만 0.2~0.5초 milliseconds 단위이기에 큰 문제는 없다고 한다. 하지만 공격자 입장에서는 1초에 몇억 단위의 digest를 얻지만 한 회당 0.2초~0.5초가 추가적으로 걸리기에 치명적이라 할 수 있다.

### ◼ Salt

Key Stretching을 한다고 해도, 각 횟수별 digest는 Rainbow table에 존재할 확률이 있다. 이를 방지하기 위해 Salt의 개념을 도입한다.

salt는 간을 치는 것처럼, Client가 입력한 정보에 다른 값을 대입하거나 추가하여, Hash Function에 주입을 한다.  
간단한 예로, Client1의 salt value는 abcd 이고, 입력한 데이터가 1234를 한다면, 1234abcd를 Hashing하는 것이다. 그런다면 기존 1234를 해싱한 값과 다른 digest가 나올 것이고, 공격자는 더 찾기 어렵게 되는것이다.

### 대표적인 알고리즘

- PBKDF2
- bcrypt
- scrypt
