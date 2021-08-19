---
date: 2021-08-19
title: "Spring Boot vscode에서 개발하기"
categories:
  - 개인공부
  - springboot
tags:
  - spring
  - springboot
---

![spring_boot_logo](https://rnrudxo2872.github.io/assets/images/springboot/spring_boot_logo.png)  
<br>
vscode를 애용했던 만큼, 이클립스 기반 STS는 나에게 너무 답답했다. legacy 버전은 vscode로 이용하기 힘들었던 만큼, 이제 spring boot는 vscode로 사용하고자 한다.

## 확장 설치

![extentions](https://rnrudxo2872.github.io/assets/images/springboot/spring_boot_vscode_setting.png)  
<br>
위와 같이 많은 확장들을 설치했다. 찾아보니 개인마다 차이가 있었으나, 처음인 만큼 만반의 준비(?)를 하기위해 이렇게 구성했다.

## JDK 설정

vscode에는 기본으로 jdk가 설정이 되어있지 않다. 그래서 직접 해줘야한다.  
window를 사용한다면 <code>ctrl + shift + p</code>, mac 사용자라면 <code>⇧ ⌘ P</code> 를 입력하여 명령 팔래트에 settings를 입력한다.  
![settings_view](https://rnrudxo2872.github.io/assets/images/springboot/settings_view.png)  
<br>
위와 같이 최상단에 표시된 json 파일을 열고, 마지막에 <code>"java.home": "본인이 설치한 jdk 경로",</code>를 입력하면 끝이다.

## Spring Boot 프로젝트 만들기

다시 명령팔래트를 열어 아래 그림과 같이 입력한다.  
![create_project_comm](https://rnrudxo2872.github.io/assets/images/springboot/springboot_generate_comm.png)  
<br>
위 그림과 같이 maven 또는 gradle 프로젝트 중 하나를 생성할 수 있다.
그 후, 개인의 요구사항에 맞게 설정을 한 후, 프로젝트 생성을 완료한다.

처음 설정이 힘들었던 만큼 다른사람에게 도움이 되고자 글을 쓴다.
