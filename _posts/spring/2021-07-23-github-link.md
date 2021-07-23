---
date: 2021-07-23
title: "Spring STS에서의 github 프로젝트"
categories:
  - 개인공부
  - spring
tags:
  - spring
  - Git
  - Github
---

![spring_logo](https://rnrudxo2872.github.io/assets/images/spring/spring_logo.png)

## repository 생성 또는 참가

처음에 필요한 것은 github의 repository다. 혼자 프로젝트를 진행한다면 본인이 직접 만들고, 팀 단위라면 팀장이 만든 repository에 collaborator로 권한을 얻고 참가한다.  
팀원의 초대 과정은 [eclipse와 github 연동 및 팀 프로젝트 진행](https://rnrudxo2872.github.io/git/eclipse/eclipse-github-team/)을 참고하기 바란다.

---

## STS에서 repository 생성, 연결하기

STS에서 repository를 연결해서 프로젝트를 import하기 위해, clone을 해야한다.  
Git Repository탭에서 등록해야하는데, 아래와 같이 진행한다.  
![show_view-other](https://rnrudxo2872.github.io/assets/images/spring/git-pro/show_view-other.png)  
![show_view-git_repo](https://rnrudxo2872.github.io/assets/images/spring/git-pro/show_view-git_repositories.png)  
<br>

그리고 탭에 있는 <code>Clone a Git repository</code>를 클릭한 후, 아래와 같이 url을 등록하여 진행한다.

<br>

![click_clone_repo](https://rnrudxo2872.github.io/assets/images/spring/git-pro/click_clone_git_repo.png)  
![clone_repo](https://rnrudxo2872.github.io/assets/images/spring/git-pro/clone_git_repo.png)
<br>
뒤에 2가지 정도 설정창이 더 나오는데 기본값으로 진행하면 된다.  
이후 생성된 repository에서 Import Project를 클릭하여 다음과 같이 진행한다.
<br>

![import_project_archive](https://rnrudxo2872.github.io/assets/images/spring/git-pro/click_import_project.png)  
![import_project_archive](https://rnrudxo2872.github.io/assets/images/spring/git-pro/import_project_archive.png)
<br>

이제 Package Explorer탭에 가본다면 원격 프로젝트를 볼 수 있을 것이다.  
여기서, 본인 프로젝트는 <code>.gitignore</code>에 .settings 파일을 제외 시켰으므로 프로젝트의 <code>Deployment Assembly</code>를 등록해줘야한다.  
아래와 같이 과정을 진행한다.

![set_project_properties](https://rnrudxo2872.github.io/assets/images/spring/git-pro/project_click_properties.png)

![no_exists](https://rnrudxo2872.github.io/assets/images/spring/git-pro/no_exists_dep.png)  
위와 같이 컴포넌트가 없다고 한다. **project facets**탭으로 가도록 하자.
<br>
<br>

![set_project_facets](https://rnrudxo2872.github.io/assets/images/spring/git-pro/set_project_facets.png)  
톰캣 8.5를 사용하고 있다면 Dynamic Web Module을 **2.5**버전 Java는 **1.8**버전을 하니 잘 구동 되었다.
