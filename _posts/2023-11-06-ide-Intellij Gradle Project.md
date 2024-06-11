---
title : "Intellij Gradle Project"
excerpt : "Intellij Gradle Project"
toc : true
toc_sticky : true
toc_label : "Intellij Gradle Project"
categories:
- IDE
tags:
- [IDE, Project]
last_modified_at: 2023-11-06T08:00:00-10:00:00
---
  
---
  
IntelliJ에서 Gradle Project를 생성해보도록 하겠다. new > Project에서 생성한 Gradle 기본 프로젝트 폴더 구조는 아래와 같다. 
{: .notice}  
  
![image](../../assets/images/intelliJGradleProject.png)
  
## 각 파일 별 역할

| 파일명                       | 역할                                                               |
| ------------------------- | ---------------------------------------------------------------- |
| gradlew                   | linux, Mac용 실행 [shell](../../developcommon/developcommon-shell) Script 파일                               |
| gradlew.bat               | Window 용 실행 [shell](../../developcommon/developcommon-shell) Script 파일                                  |
| gradle-wrapper.properties | JAR 형식으로 압축된 Wrapper 파일<br>Gradle Task 실행                        | 
{: .notice}  
| build.gradle              | 프로젝트의 라이브러리 의존성, 플러그인, 라이브러리 저장소 등을 설정할 수 있는 Build Script        |
| setting.gradle            | 프로젝트의 구성정보 파일<br>멀티 프로젝트를 구성하여 프로젝트를 모듈화 할 경우, 하위 프로젝트의 구조 설정 가능 | 
{: .notice}  

---
  
# 연결문서
- [Intellij](../../ide/ide-Intellij)
- [Gradle](../../build/build-Gradle)