---
title: "Gradle"
excerpt: "오픈 소스 빌드 도구"

categories:
- ServerProgramming

tags:
- [ServerProgramming]

toc: true
toc_sticky: true
toc_label: "Gradle"

last_modified_at: 2022-10-20T08:00:00-10:00:00
---
# Gradle 이란?
  - 유연성과 성능에 중점을 둔 오픈 소스 빌드 자동화 도구

# Gradle의 장점
  - 다른 빌드 도구에 비해 속도가 빠르다.
  - 높은 수준의 커스터마이징 기능을 제공한다.

# 다른 빌드 도구
  - Ant
  - Maven

# Gradle의 라이브러리 dependency 관리
  ![image](/assets/images/ServerProgramming/Gradle_Dependency_Administration.png){: width="50%" height="50%"}

## 용어설명
  - artifact : 개발 프로세스에 의해 생성 된 모든 결과물 (빌드 도구에서는 주로 '.jar' 파일을 의미한다.)
  - repository : 의존성 모듈들의 온라인 저장소 (Maven, Ivy)

## Gradle 동작
  - 특정 task를 실행하기 위해 필요한 dependency들을 런타임에 원격 저장소에서 다운로드 받거나 로컬 저장소에서 가져온다.(dependency resolution)
  - 향후 불필요한 네트워크 호출을 줄이기 위해 의존성 파일들을 dependency cache에 저장한다.

---

# build.gradle
  - 이제 build.gradle 파일의 Syntax를 분석해보겠다. 아래 소스는 Gradle 프로젝트 생성시 default로 생성되는 Gradle 소스이다.
  
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

  ```

## plugins
  - 프로젝트의 모든 모듈에 공통되는 Gradle Task의 집합
  - Task는 앱 빌드부터 테스트까지 다양한 작업을 수행하는 작업단위이며, 앱의 타입 명시하면 관련된 Task들을 자동으로 추가한다.

## repositories
  - '어떤 저장소를 사용할 것인가' 에 대한 정의
  - mavenCentral() => Maven Central
  - jcenter() => Bintray JCenter
  - google() => Google Android
  - 대표적으로 3가지를 주로 사용하며 이외에도 많은 저장소가 있다. ==> [go to MavenRepo](https://mvnrepository.com/repos)

### mavenCentral vs jcenter
  - jcenter는 mavenCentral보다 라이브러리 업로드가 쉽다.
  - jcenter에 업로드시, mavenCentral에 동기화 설정도 가능하다.

## dependencies
  - 저장소에 필요한 라이브러리 항목 정의
  - sprint boot 프로젝트의 경우 starter을 통해 버전관리를 쉽게 할 수 있다.

### testImplementation
  - 테스트 코드를 수행할 때 적용되는 의존 라이브러리

### implementation
  - 컴파일 시 적용되는 모듈의 의존 라이브러리
  - 빌드 출력에 의존 라이브러리를 패키징
  - 모듈의 의존 라이브러리 수정시, 수정된 모듈에 직접적으로 의존하는 모듈만 재빌드

### api
  - 컴파일 시 적용되는 모듈의 의존 라이브러리
  - 빌드 출력에 의존 라이브러리를 패키징
  - 모듈 의존 라이브러리 수정시, 수정된 모듈과 관련된 모든 모듈이 재빌드

### compileOnly
  - 컴파일 시에만 사용

### runtimeOnly
  - 런타임에만 사용

## dependencies 추가하기
  - MavenCentral을 예시로 추가할 dependency 구문을 찾아보자
  - [MavenCentral](https://mvnrepository.com/) 로 이동
  - 내가 사용하고자 하는 artifact 검색, 좌측 리스트에서 검색 옵션 설정 가능  
  ![image](/assets/images/ServerProgramming/Gradle_Dependency_SearchResult.png){: width="70%" height="70%"}  
  - 위 화면에서 원하는 artifact를 선택하면, 버전리스트를 확인할 수 있다.  
  ![image](/assets/images/ServerProgramming/Gradle_Dependency_SelectVersion.png){: width="70%" height="70%"}  
  - 위 화면에서 특정 버전을 선택 후, gradle 탭을 선택하면, 아래 텍스트박스에 gradle 소스를 확인 할수 있다.  
  ![image](/assets/images/ServerProgramming/Gradle_Dependency_Code.png){: width="70%" height="70%"}  

  - 소스를 복사해서 build.gradle 파일에 붙여넣으면 끝!


