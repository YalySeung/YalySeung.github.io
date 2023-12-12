---
title : "Gradle"
excerpt : "Gradle"
toc : true
toc_sticky : true
toc_label : "Gradle"
categories:
- Build
tags:
- [Build]
last_modified_at: 2023-10-15T08:00:00-10:00:00
---

# 날짜 : 2023-10-15 22:47

# 태그 : #Build 
---

# 내용

## 환경
- JDK 또는 JRE 8 이상
- 인터넷 사용환경

## Gradle Process
  
![image](./../../assets/images/../../assets/Images/GradleProcess.png)

## Gradle Script Sample

```groovy
plugins {
    id 'application' 
}

repositories {
    mavenCentral() 
}

dependencies {
    testImplementation 'org.junit.jupiter:junit-jupiter:5.9.3' 

    testRuntimeOnly 'org.junit.platform:junit-platform-launcher'

    implementation 'com.google.guava:guava:32.1.1-jre' 
}

application {
    mainClass = 'demo.App' 
}

tasks.named('test') {
    useJUnitPlatform() 
}
```

## 의존성 관리

### repositories
- 저장소 설정
- 클로저의 내용은 RepositoryHandler 를 통해서 실행됨
- mavenCentral 메소드와 jcenter 메서드 제공

### ext 메소드
- 인자를 buildScript에서 전역 변수로 사용할 때 필요

### dependencies
- 의존성 라이브러리를 추가할 때 사용

#### implementation
- 의존 라이브러리 수정시 본 모듈까지만 재빌드

#### api
- 의존 라이브러리 수정시 본 모듈을 의존하는 모듈들을 전부 재빌드

#### compileOnly
- compile시에만 빌드하고 빌드 결과물에는 포함하지 않음

#### testImplementation
- 테스트 코드를 수행할 때만 적용

#### annotation processor
- annotation processor 명시

## task
- 빌드, 테스트, 배포 등의 단계를 수행하는 작업 단위
- build.gradle task 블록 내에서 정의
- doFirst, doLast : task 내부에서 순서 지정

## plugins
- 빌드와 배포 프로세스를 확장하는데 사용
- java 컴파일, 테스트, [JAR](../../java/java-JAR) 패키징 등의 task 제공

## 빌드 속도가 빠른 이유

### 점진적 빌드
- 바뀐 파일들만 빌드
- 빌드 실행중, 마지막 빌드 호출 이후에 task 입력, 출력 혹은 구현이 변경됐는지 확인

### build cache
- 하나의 빌드에서 사용되는 파일들이 다른 빌드들에 사용된다면 빌드 캐시를 사용해서 한번만 다운로드 또는 빌드

### Daemon Process
- 메모리상에 빌드 결과물을 보관
- 한번 빌드된 프로젝트는 다음 빌드에 매우 적은 시간만 소요됨
- [Daemon Process](../../ServerCommon/ServerCommon-Daemon-Process)

---

# 연결문서
