---
date: 2021-06-11
title: "eclipse와 github 연동 및 팀 프로젝트 진행"
categories:
  - Git
tags:
  - git
  - eclipse
  - 팀프로젝트
---

# collaborator 얻기

협동작업을 위해 collaborator를 초대하거나, 다른 사람에게 초대받는다.  
![초대](https://rnrudxo2872.github.io/assets/images/github/invit_github.png)  
초대를 받으면 위와 같은 메일을 받을 수 있을 것이다. View invitation을 눌러 레포지토리를 확인한다.

만약 나의 레포지토리에서 편하게 확인, 또는 가지고 오고 싶다면, fork로 긁어와줘도 된다.  
![fork](https://rnrudxo2872.github.io/assets/images/github/git_hub_fork.png)

---

# eclipse와 github 연동

우선 이클립스를 실행시킨후, 프로젝트 explorer에 우클릭을 한다.  
![eclips_github](https://rnrudxo2872.github.io/assets/images/github/github_eclipse_1.png)  
import를 클릭한 후,

![eclips_github](https://rnrudxo2872.github.io/assets/images/github/github_eclipse_2.png)  
git을 검색한 후, Project from Git을 선택한다.

![eclips_github](https://rnrudxo2872.github.io/assets/images/github/github_eclipse_3.png)  
![eclips_github](https://rnrudxo2872.github.io/assets/images/github/github_eclipse_4.png)  
진행하다 보면 위와 같은 원격 저장소의 URL을 입력하라고 할 것이다.  
해당 저장소의 URL을 복사 해준 후, eclipse의 요구란에 넣어준다.

![eclips_github](https://rnrudxo2872.github.io/assets/images/github/github_eclipse_5.png)  
그 다음에 위와 같이 저장소에서 어떤 branch를 가져올 것인지 물어볼 것이다. branch는 다음 포스팅에서 다뤄보고, 우선 다 불러준다.

![eclips_github](https://rnrudxo2872.github.io/assets/images/github/github_eclipse_6.png)  
어떤 branch를 선택하고 시작할 것인지 묻는 화면이다. 우선 master로 선택하고, 후에 분업을 위해 branch를 만드는 작업을 할 것이다.  
후에 다른 설치 과정은 Next로 진행해준다.

![eclips_github](https://rnrudxo2872.github.io/assets/images/github/github_eclipse_6.png)  
모든 과정을 완료하면, 위와같이 원격 저장소의 파일들을 eclipse에 불러온 것을 볼 수 있다.
