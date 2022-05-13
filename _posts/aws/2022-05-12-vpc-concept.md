---
date: 2022-05-12
title: VPC가 무엇일까
categories:
  - 개인공부
  - aws
tags:
  - aws
  - vpc
  - vpn
---

aws에서 마주치는 vpc는 무엇인가 궁금하여, 그에 대해 간단히 작성하고자 합니다.
<br>

# VPN(Virtual Private Network)

VPC를 알기 전, VPN을 먼저 개념 정리를 하고자 합니다.
VPN을 번역하면 "가상사설망"이라고 합니다. "가상"이라는 단어에서 유추할 수 있는데, **가상의 사설망**입니다.

<br>
사내 네트워크망을 사용중 일 때, 보안상의 이유로 직원간 네트워크를 분리하고 싶다면 기존 인터넷선 선 분리를 직접해야 합니다. 이러한 물리적인 분리 작업을 피하기 위해 가상의 망 VPN을 사용하게 됩니다.

<br>

# VPC(Virtual Private Cloud)

> Amazon Virtual Private Clud(Amazon VPC)를 이용하면 사용자가 정의한 가상 네트워크로 AWS 리소스를 시작할 수 있습니다. 이 가상 네트워크는 AWS의 확장 가능한 인프라를 사용한다는 이점과 함꼐 고객의 자체 데이터 센터에서 운영하는 기존 네트워크와 매우 유사합니다. <br> - Amazon VPC documentation 출처

<br>
즉, 사용자가 정의하는 IP 주소 범위 선택, 서브넷 생성, 라우팅 테이블 및 네트워크 게이트웨이 구성 등 가상 네트워킹 환경을 VPC라고 합니다.

<br>

![no-vpc](https://rnrudxo2872.github.io/assets/images/aws/no-vpc.png)
<sub>VPC가 없을 때</sub>

<br>

VPC가 없다면 EC2 인스턴스들이 서로 거미줄처럼 연결되고 인터넷과 연결 됩니다. 이런 구조는 시스템의 복잡도를 상승시키며, 하나의 인스턴스만 추가되도 모든 인스턴스를 수정해야하는 불편함이 생길 수 있습니다. 마치 인터넷 선을 수정해야 하는 것과 유사합니다.

<br>

![exist_vpc](https://rnrudxo2872.github.io/assets/images/aws/exist_vpc.png)

<br>

VPC를 적용하면 위 그림과 같이 VPC 별로 네트워크를 구성할 수 있고 각각의 VPC에 따라 다르게 네트워크 설정을 줄 수 있습니다. 또한 각각의 VPC는 완전히 독립된 네트워크처럼 동작하게 됩니다.

<sub>그림 출처 및 참고: [https://medium.com/harrythegreat/aws-%EA%B0%80%EC%9E%A5%EC%89%BD%EA%B2%8C-vpc-%EA%B0%9C%EB%85%90%EC%9E%A1%EA%B8%B0-71eef95a7098](https://medium.com/harrythegreat/aws-%EA%B0%80%EC%9E%A5%EC%89%BD%EA%B2%8C-vpc-%EA%B0%9C%EB%85%90%EC%9E%A1%EA%B8%B0-71eef95a7098)</sub>
