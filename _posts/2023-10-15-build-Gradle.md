---
title : "Gradle"
excerpt : "Gradle"
toc : true
toc_sticky : true
toc_label : "Gradle"
categories:
- Build
tags:
- [BuildManager]
last_modified_at: 2023-10-15T08:00:00-10:00:00
---
  
---
  
> **Gradle이란?**  
>
> CI/CD를 위해 아래 작업들을 자동화 시켜 주는 **Groovy 기반의 오픈소스 빌드 도구**이다. 
{: .notice--info}  
  
## Gradle을 사용하는 이유
  
### 점진적 빌드
- 바뀐 파일들만 빌드
- 빌드 실행중, 마지막 빌드 호출 이후에 task 입력, 출력 혹은 구현이 변경됐는지 확인
  
### build cache
- 하나의 빌드에서 사용되는 파일들이 다른 빌드들에 사용된다면 빌드 캐시를 사용해서 한번만 다운로드 또는 빌드
  
### Daemon Process
- 메모리상에 빌드 결과물을 보관
- 한번 빌드된 프로젝트는 다음 빌드에 매우 적은 시간만 소요됨
- [Daemon Process](../../servercommon/servercommon-Daemon-Process)
  
## Gradle Process
  
![image](../../assets/images/GradleProcess.png)

 위 이미지는 Gradle이 원격 레포지토리에서 **artifact**를 가져와서 **캐싱**하는 과정을 보여준다. **Gradle Refresh**를 하면, Gradle은 build.gradle 파일의 레포지토리에 명시된 외부 artifact를 요청하여 가져온다. 이 artifact들은 Gradle 내부적으로 **Cache에 저장**되고 기존과 동일한 artifact일 경우 cache에 있는 artifact를 사용한다. 
  
## Gradle Syntax
 이제 .gradle 파일 작성법을 살펴보자. .gradle 파일은 **groovy 스크립트**를 작성해야한다. 아래 text는 .gradle 샘플 스크립트이다.
  
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

 위 스크립트의 내용을 기반으로 각 항목별 기능을 알아보자. 

 **plugins** 항목은 빌드와 배포 **프로세스를 확장**하는데 사용한다. **java 컴파일**, **테스트**, **JAR 패키징** 등의 task를 확장할 수 있다.

 **repositories** 항목은 **artifact를 가져올 저장소**를 명시해주는 부분이다. 위 스크립트에서는 mavenCentral 저장소를 사용했다. 

 **dependencies** 항목은 프로젝트에 추가할 **의존성 라이브러리 목록**을 명시한다. 라이브러리 추가시, 옵션은 아래와 같다.

| Keyword             | 기능                                  |
| ------------------- | ----------------------------------- |
| implementation      | 의존 라이브러리 수정시 본 모듈까지만 재빌드            |
| api                 | 의존 라이브러리 수정시 본 모듈을 의존하는 모듈들을 전부 재빌드 |
| compileOnly         | compile시에만 빌드하고 빌드 결과물에는 포함하지 않음    |
| testImplementation  | 테스트 코드를 수행할 때만 적용                   |
| annotationProcessor | annotation processor 명시             |

 **tasks**는 빌드, 테스트, 배포 등의 단계를 수행하는 작업단위를 의미한다. task 내부에서 doFirst, doLast를 통해 순서를 지정 할 수 있다.

---
  
# 연결문서
- [Java BuildTools](../../build/build-Java-BuildTools)