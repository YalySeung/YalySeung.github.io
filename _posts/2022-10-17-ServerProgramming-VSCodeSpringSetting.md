---
title: "VSCode Spring Lagacy Setting"
excerpt: "VSCode로 Spring Lagacy 개발환경 셋팅하기!"

categories:
- ServerProgramming

tags:
- [ServerProgramming]

toc: true
toc_sticky: true
toc_label: "VSCode Spring Lagacy Setting"

last_modified_at: 2022-10-17T08:00:00-10:00:00
---
# 개요
  - 서버 개발시, 무거운 Eclipse 대신 VSCode를 사용하여 개발하고자 하는 사람들을 위한 환경셋팅 방법을 소개하겠다.

# 환경셋팅
## VSCode 확장 프로그램 설치
  - Extention Pack for Java 설치
  ![image](/assets/images/ServerProgramming/JavaExtention.png)

  - Gradle 사용을 위한 Gradle For java 설치
  ![image](/assets/images/ServerProgramming/GradleExtention.png)

# Java App 프로젝트 생성
  - Ctrl + Shift + P 모든 명령 표시 화면에서 gradle 입력 후 Create a Gradle Java Project(Advanced) 항목을 선택한다.  
  ![image](/assets/images/ServerProgramming/CreateGradleProject.png)

  - 프로젝트 폴더 경로를 설정한 후 아래와 같이 진행한다.
  ![image](/assets/images/ServerProgramming/Gradle_SelectProjectType.png)
  ![image](/assets/images/ServerProgramming/Gradle_SelectScriptDSL.png)
  ![image](/assets/images/ServerProgramming/Gradle_SelectTestFramework.png)
  ![image](/assets/images/ServerProgramming/Gradle_InsertProjectName.png)
  ![image](/assets/images/ServerProgramming/Gradle_InsertPackage.png)

  - 생성 결과  
  ![image](/assets/images/ServerProgramming/CreateGradleProjectResult.png)

# Java App 프로젝트 실행
  - main 소스의 App.java 파일을 우클릭하여 Run Java를 선택한다.
  ![image](/assets/images/ServerProgramming/RunGradleProject.png)
  
  - 실행결과  
  ![image](/assets/images/ServerProgramming/RunJavaResult.png)

  Gradle : 7.3, JDK : 17 버전으로 자동 셋팅되어 빌드되었다. Spring Lagacy 셋팅은 추후에 업데이트 할 예정..


  
