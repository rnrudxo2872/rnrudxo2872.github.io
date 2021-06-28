---
date: 2021-06-29
title: "Go 프로젝트 만들기"
categories:
  - Go
tags:
  - Go
  - Go Project
---

## GoLang? golang?

![go_logo](https://rnrudxo2872.github.io/assets/images/go/go_logo.png)  
golang은 2007년 구글에서 개발한 언어이다. Go라고 부르면 된다. 언어 자체에서 GC(galbage cllection)을 지원하며, 고루틴이라는 동시성 프로그래밍을 제공한다고 한다.

---

## 특징

일단 python, javascript보다 빠르다. 성능테스트한 자료를 본적 있는데 대략 2배에서 심하게는 100배 이상 차이가 났다.  
reference도 java나 다른 언어들보다 양이 매우 작다. java의 1/7정도?  
가벼운만큼 프로젝트를 시작하는 과정도 너무 간단하다.

---

## Go 프로젝트

하나의 언어이니, 여러 특징들을 설명하면 정말 양이 많다.  
언어의 특징은 후에 더 자세히 찾아보도록 하고, 프로젝트를 시작해 보자.  
우선, 당연하지만 [언어를 설치](https://golang.org/)해야한다. 링크를 눌러 공식 페이지에서 다운로드를 클릭하면 직관적으로 잘 구성되어 있다. <br/>  
본인 환경에 맞춰 설치 후, 콘솔창에 go version을 입력하면,

```bash
$> go version
go version go1.16.5 [본인 운영체제]
```

위에 방식으로 출력된다면 정상적으로 설치가 된 것이다.  
그 후에 go 프로젝트를 만들어 보기전, vscode를 이용하는 나는 go 확장팩을 설치하였다.  
![go_extension](https://rnrudxo2872.github.io/assets/images/go/go_extension.png)

---

이제 본인의 프로젝트 폴더에서

```bash
go mod init github.com/[본인url]
```

명령어를 콘솔창에서 입력해준다면 go.mod가 생성된다. 이제 main.go로 프로젝트를 시작하면 된다.
