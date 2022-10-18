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

  Gradle : 7.3, JDK : 17 버전으로 자동 셋팅되어 빌드되었다.

# 탐색기에서 수정이 필요없는 파일 or 폴더 숨기기, 검색 제외하기
## VSCode setting.json 파일 수정
  - Ctrl + Shift + p => 설정 파일 open  
  ![image](/assets/images/ServerProgramming/VSCodeUserSettingContext.png)  
  - json Editting  
  ![image](/assets/images/ServerProgramming/VSCodeUserSettingJson.png)  
  - files.exclude, search.exclude 항목 추가  
  ![image](/assets/images/ServerProgramming/VSCodeHideFilesFolders.png)

  ```
    "files.exclude": {
        "**/.classpath": true,
        "**/.project": true,
        "**/.settings": true,
        "**/.factorypath": true,
        ".gradle": true,
        "app/tomcat.8080": true
    },

    "search.exclude": {
        "**/.classpath": true,
        "**/.project": true,
        "**/.settings": true,
        "**/.factorypath": true,
        ".gradle": true,
        "app/tomcat.8080": true
    }
  ```
  
# Java EE 웹 어플리케이션으로 변환
  - WebApp 폴더 추가
  - gradle 의존성 라이브러리 추가 [의존성라이브러리 정보 링크](https://mvnrepository.com/)
  
  ```groovy
  plugins {
    id 'war'
  }

  repositories {
      jcenter()
  }

  dependencies {
      testImplementation 'org.junit.jupiter:junit-jupiter:5.7.0'
      testRuntimeOnly 'org.junit.jupiter:junit-jupiter-engine:5.7.0'

      compileOnly 'javax.servlet:javax.servlet-api:4.0.1'
      compileOnly 'javax.servlet.jsp:javax.servlet.jsp-api:2.3.3'

      implementation 'org.glassfish:javax.json:1.1.4'
      implementation 'org.apache.logging.log4j:log4j-api:2.13.1'
      implementation 'org.apache.logging.log4j:log4j-core:2.13.1'

      annotationProcessor 'org.apache.logging.log4j:log4j-api:2.13.1'
      annotationProcessor 'org.apache.logging.log4j:log4j-core:2.13.1'
  }
  ```

  - gradle 파일을 수정하면 아래와 같은 팝업이 뜨는데 Yes 또는 Always를 선택한다.
  ![image](/assets/images/ServerProgramming/GradleChangedPopup.png)
  
  - Gradle 탭으로 이동하면 실행 가능한 Gradle Task 들을 확인할 수 있다.
  ![![image]](/assets/images/ServerProgramming/GradleTask.png)


남은 JavaEE 셋팅은 이후 수정 예정...