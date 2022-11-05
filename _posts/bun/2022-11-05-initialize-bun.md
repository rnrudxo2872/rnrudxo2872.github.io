---
date: 2022-11-05
title: Bun를 설치해보자
categories:
- 개인공부
tags:
- Bun
- javascript
---

# Bun은 무엇일까?
Bun은 javascript 엔진입니다. Node.js와 Deno와 같이 브라우저 외에서 JS를 사용할 수 있도록 만들어진 런타입니다.  
아래와 같은 세 가지 요소를 중점으로 둔다고 합니다.
- Start fast
- New levels of performance
- Being a great and complete tool

출처: [https://bun.sh/](https://bun.sh/)  

<br>

기존 Node.js에서 사용하던 것을 대부분 사용할 수 있다고 합니다. (대략 90% 구현)  
만들어진 언어는 zig라는 언어로 구현되어 있는걸로 알고 있습니다. zig로 기존에 있던 숨겨진 제어 흐름이 없애고, 저수준의 메모리 제어를 통해라고 합니다.

# 설치 진행
bash 명령어로 간단히 설치할 수 있습니다.
```bash
curl https://bun.sh/install | bash
```

windows 운영체제를 사용한다면, wls를 설치해야 합니다.

혹시 unzip이 없다는 에러가 출력되면, 아래와 같은 명령어를 입력합니다.
```bash
sudo apt install unzip
```

해당 설치를 완료 후, 아래와 같은 화면을 볼 수 있습니다.
![설치 완료 화면](https://rnrudxo2872.github.io/assets/images/bun/result_install_bun.png)

bun 명령어를 잘 사용할 수 있도록 .bashrc를 수정해 줍시다.
```bash
vim ~/.bashrc

# bun 명령어 추가
export BUN_INSTALL="$HOME/.bun"
export PATH="$BUN_INSTALL/bin:$PATH"
```
이후 변경사항을 적용하기 위해, 아래의 명령어를 입력해 줍시다.
```bash
source ~/.bashrc
# 혹은
. ~/.bashrc
```

이후 다시 "bun"을 입력하면 후, 아래와 같은 결과가 출력된다면 설치가 되었습니다.
![설치 완료 화면](https://rnrudxo2872.github.io/assets/images/bun/complete_bun.png)