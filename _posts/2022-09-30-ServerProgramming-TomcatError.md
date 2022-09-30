---
title: "Apache Tomcat Error"
excerpt: "Apache Tomcat 에러 모음"

categories:
- ServerProgramming

tags:
- [ServerProgramming]

toc: true
toc_sticky: true
toc_label: "Apache Tomcat Error"

last_modified_at: 2022-09-30T08:00:00-10:00:00
---
# 개요
  - Apache Tomcat을 사용하며 경험해본 에러에 관해 정리해보겠다.

# 404 Error
  - 서버 개발 뉴비가 혼자 유튜브를 보며 실습을 하는 과정에서 에러가 발생했다.
  
  ![image](/assets/images/ServerProgramming/404Error.png)

  소스코딩 없이 단지 Tomcat 서버만 실행했을 뿐인데.. 고양이를 보고싶었을 뿐인데.. 404 에러 발생ㅜ 일단 404 에러의 원인을 찾아보자..

  - 404 에러 : "서버 자체가 존재"하지만 서버가 응답한 페이지를 찾지 못 했을때 나는 오류
  
  localhost:8080 으로 request 하면 어느 페이지로 연결 되는지 찾아보자.

  ![image](/assets/images/ServerProgramming/TomcatWebModuleMapping.png)

  Tomcat 서버를 더블클릭 -> Module 탭으로 이동하면 위와같은 화면을 볼 수 있다.
  여기에 request 시, 불러올 jsp 파일을 맵핑한다.

  ![image](/assets/images/ServerProgramming/SetIndexJsp.png)

  Tomcat 설치경로에 가면 고양이 jsp 페이지를 찾을 수 있는데, 이 폴더 경로를 루트 Path로 지정한다.
  저장 후 재시작해보면?

  ![image](/assets/images/ServerProgramming/TomcatIndexPage.png)

  고양이 등장!
