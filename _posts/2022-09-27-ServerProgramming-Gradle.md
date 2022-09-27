---
title: "Gradle"
excerpt: "오픈 소스 빌드 자동화 도구"

categories:
- ServerProgramming

tags:
- [ServerProgramming]

toc: true
toc_sticky: true
toc_label: "Gradle"

last_modified_at: 2022-09-27T08:00:00-10:00:00
---
# 개요
  - Gradle 개념 정리
  - Gradle Syntax 정리

# Gradle 이란?
  - 유연성과 성능에 중점을 둔 오픈 소스 빌드 자동화 도구

# Gradle의 장점
  - 속도 빠름
  - 높은 수준의 커스터마이징 기능 제공

# Gradle Syntax 구조
  - Gradle 파일은 Project Object 객체로 Project 인터페이스를 구현하는 구현체
  - Project 오브젝트는 Project 단위에서 필요한 작업을 수행하기 위해 모든 메서드와 프로퍼티를 모아놓은 슈퍼 객체
  
  ```java
    public interface Project extends Comarable<Project>, ExtensionAware, PluginAware{
      ...
    }
  ```

---

## Gradle의 메서드

### 메서드 정의
  - 아래는 Gradle 프로젝트를 생성하면 만들어지는 groovy 형태의 build.gradle 파일이다.
  
  ```groovy
    plugins {
      id 'java-library'
    }

    repositories {
      mavenCentral()
    }

    dependencies {
      testImplementation 'org.junit.jupiter:junit-jupiter:5.8.1'
      api 'org.apache.commons:commons-math3:3.6.1'
      implementation 'com.google.guava:guava:30.1.1-jre'
    }

    tasks.named('test') {
      useJUnitPlatform()
    }
  ```
  - <span style="color:red">plugins, repositories, dependencies, tasks.named('test')</span> 각각은 하나의 메서드이며, Gradle 빌드시 이 메서드들이 수행된다.
  - {}로 감싸진 부분은 Groovy의 클로저(Closure) 이며, 위와 같이 메서드를 인자로 전달할 수 있다.

### 커스텀 메서드 정의
  - Groovy 의 ext와 Closure를 사용하여 정의

  ``` groovy
    ext.[MethodName] = { parma1, param2 -> [body] }
    project.ext.[MethodName] = { parma1, param2 -> [body] }
  ```

---

## Gradle의 프로퍼티
### 프로퍼티 정의
  
  ``` groovy
    project.[PropertyName] = [값]
    [PropertyName] = [값]
  ```

  - 위의 방식은 Project 객체에 미리 정의된 프로퍼티만 재정의 가능하다.

### 커스텀 프로퍼티
  - project 객체에 extention을 넣는 방식으로 정의
  
  ``` groovy
    project.ext.[PropertyName] = [값] // 정의
    project.[PropertyName] // 값 꺼내오기
  ```
