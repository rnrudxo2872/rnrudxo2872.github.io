---
date: 2021-06-11
title: "eclipse에서 git branch 생성 및 commit, push"
categories:
  - Git
  - eclipse
tags:
  - git
  - eclipse
  - 팀프로젝트
---

## Git Branch 생성

협동(협업) 작업에서 branch를 활용한 작업들은 필수 요소이다. branch를 활용한 workflow 전략은 거의 교과서처럼 잡혀있다.  
eclipse에서도 협동 작업을 위해 branch를 생성한 후, commit and push로 내가 한 작업을 새로 만든 branch에 올려다 보는 과정을 진행하겠다.

---

## branch 생성

![branch-commit](https://rnrudxo2872.github.io/assets/images/github/eclipse/branch_commit_push_1.png)  
eclipse에 레포지토리와 연동된 project를 우클릭후, 위와 같이 New Branch를 클릭해 준다.

![branch-commit](https://rnrudxo2872.github.io/assets/images/github/eclipse/branch_commit_push_2.png)  
본인이 따로 작업할 branch의 명을 입력한다.  
![branch-commit](https://rnrudxo2872.github.io/assets/images/github/eclipse/branch_commit_push_3.png)  
그 후, 다시 Switch To를 본다면 본인의 branch가 만들어지고 자동으로 해당 branch를
사용하도록 적용되어 있을것이다.

---

## commit, push

이제 본인이 작업을 한 뒤, 해당 저장소에 올리는 과정을 진행한다.  
아래와 같이 test폴더를 생성 후, hello.jsp 파일을 만드는 작업을 했다고 가정한다.  
![branch-commit](https://rnrudxo2872.github.io/assets/images/github/eclipse/branch_commit_push_4.png)

![branch-commit](https://rnrudxo2872.github.io/assets/images/github/eclipse/branch_commit_push_5.png)  
이제 원격저장소에 올리기위해 해당 프로젝트를 우클릭 후, Commit를 눌러준다.

![branch-commit](https://rnrudxo2872.github.io/assets/images/github/eclipse/branch_commit_push_6.png)  
위와 같이 Git Staging이라고 현재 추적되고 있는 파일들이 어떤 상태인지 나올 것이다.
작업한 파일들(즉, 변경된 파일들)이 Unstaged Changes에 표시될 것이다. 해당 파일들을 드래그 하여 Staged Changes로 옮겨준다.

![branch-commit](https://rnrudxo2872.github.io/assets/images/github/eclipse/branch_commit_push_7.png)  
Staged Changes로 옮겨준 후, Commit 메세지를 입력, **원격 저장소에 올리기 위해서는 Commit and Push 버튼**을 클릭한다.  
![branch-commit](https://rnrudxo2872.github.io/assets/images/github/eclipse/branch_commit_push_8.png)  
그 후, 과정은 위와 같이 Next와 Finish로 마무리 한다.  
![branch-commit](https://rnrudxo2872.github.io/assets/images/github/eclipse/branch_commit_push_9.png)  
github에 정상적으로 올라간다면 위와 같은 화면이 나올 것이다.  
![branch-commit](https://rnrudxo2872.github.io/assets/images/github/eclipse/branch_commit_push_10.png)  
저장소에 정상적으로 commit, push 된다면 해당 프로젝트에 브런치가 생성되어 있을 것이다.  
![branch-commit](https://rnrudxo2872.github.io/assets/images/github/eclipse/branch_commit_push_11.png)  
해당 작업이 정상적으로 본인의 branch에 올라간 것을 볼 수 있다.
