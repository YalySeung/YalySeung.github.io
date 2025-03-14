---
title : "eclipse 폐쇄망"
excerpt : "eclipse 폐쇄망"
toc : true
toc_sticky : true
toc_label : "eclipse 폐쇄망"
categories:
- IDE
tags:
- [IDE]
last_modified_at: 2024-10-04T08:00:00-10:00:00
---
  
---
  
## 폐쇄망에서 repository 사용
 필자는 솔루션 및 SI개발자로, 금융권에 파견 근무를 나가는 경우가 있다. 금융권에서의 개발은 폐쇄망에서 이루어 지는 경우가 많아 인터넷 환경처럼 **외부 repository에 접근 할 수 없는 경우**가 대부분이다. 그래서 **local repository를 구성하여 사용**해야 하는데, 그 방법에 대해서 알아보자.

 필자는 [Gradle](../../build/build-Gradle)이 익숙하여 폐쇄망 Gradle 빌드환경을 구성할 것이다.
  
### 1. 외부망에서 maven 프로젝트 생성
 Gradle에서 Local Repository 사용을 위해서는 mavenCentral 대신 mavenLocal 을 사용해야 하는데, 이때 사용하는 경로가 C:\\Users\\사용사명￦￦.m2 이며, 이 경로의 [JAR](../../java/java-JAR) 파일이 build에 사용된다. 
 mavenlocal() 에서 사용하는 폴더 구조와 동일하게 레포지토리를 구성하기 위해 **maven build를 사용하여 빌드**한다.
  
```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"

...
  
<parent>
	<groupId>org.springframework.boot</groupId>
	<artifactId>spring-boot-starter-parent</artifactId>
	<version>2.6.0</version>
	<relativePath/> <!-- lookup parent from repository -->
</parent>
  
<properties>
	<java.version>1.8</java.version>
	<querydsl.version>4.4.0</querydsl.version>
</properties>
  
<dependencies>
	<!-- Spring Boot Web -->
	<dependency>
	<groupId>org.springframework.boot</groupId>
	<artifactId>spring-boot-starter-web</artifactId>
	</dependency>
	  
	<!-- Spring Boot Data JPA -->
	<dependency>
	<groupId>org.springframework.boot</groupId>
	<artifactId>spring-boot-starter-data-jpa</artifactId>
	</dependency>
	  
	<!-- Validation (JSR-303/JSR-380) -->
	<dependency>
	<groupId>org.springframework.boot</groupId>
	<artifactId>spring-boot-starter-validation</artifactId>
	</dependency>
	  
	<!-- Logging (using default Spring Boot Logging) -->
	<dependency>
	<groupId>org.springframework.boot</groupId>
	<artifactId>spring-boot-starter-logging</artifactId>
	</dependency>
	  
	<!-- Oracle JDBC Driver (ojdbc8) -->
	<dependency>
	<groupId>com.oracle.database.jdbc</groupId>
	<artifactId>ojdbc8</artifactId>
	<version>19.8.0.0</version>
	</dependency>
	  
	<!-- QueryDSL JPA -->
	<dependency>
	<groupId>com.querydsl</groupId>
	<artifactId>querydsl-jpa</artifactId>
	<version>${querydsl.version}</version>
	</dependency>
	  
	<!-- QueryDSL APT for Code Generation -->
	<dependency>
	<groupId>com.querydsl</groupId>
	<artifactId>querydsl-apt</artifactId>
	<version>${querydsl.version}</version>
	<scope>provided</scope>
	</dependency>
	  
	<!-- Springdoc OpenAPI UI -->
	<dependency>
	<groupId>org.springdoc</groupId>
	<artifactId>springdoc-openapi-ui</artifactId>
	<version>1.6.9</version>
	</dependency>
	  
	<!-- Springdoc OpenAPI Data REST -->
	<dependency>
	<groupId>org.springdoc</groupId>
	<artifactId>springdoc-openapi-data-rest</artifactId>
	<version>1.6.9</version>
	</dependency>
	  
	<!-- H2 Database (for testing) -->
	<dependency>
	<groupId>com.h2database</groupId>
	<artifactId>h2</artifactId>
	<scope>test</scope>
	</dependency>
</dependencies>
   
  ...
  
</project>
```

 Backend 개발에 필요한 라이브러리만 추가한다고 했는데 생각보다 많다. [Swagger](../../servercommon/servercommon-Swagger), Spring boot, [Querydsl](../../jpa/jpa-Querydsl) 관련 라이브러리들이다. 

 이렇게 설정하고 maven install 을 하면 C:\\Users\\사용자명￦￦.m2 경로에 아래와 같이 라이브러리가 잘 받아진 것을 볼 수 있다.
  
![image](../../assets/images/mavenLocalLibrary.png)

 추가로 플러그인에서 사용하는 종속성 라이브러리들은 아래와 같은 방법으로도 .m2경로에 다운로드 받을 수 있다.
  
```bash
mvn dependency:go-offline
```
  
### 2. 폐쇄망으로 repository 반입
 로컬 maven repository가 구성되었으면, 폐쇄망으로 repository를 반입하여, C:\\Users\\사용자명￦￦.m2 경로에 위치시키자.
  
### 3. Gradle 프로젝트 생성 및 설정
 Gradle 프로젝트 생성 후 build.gradle 스크립트를 작성한다.
  
```groovy
plugins {
    id 'org.springframework.boot' version '2.6.0'
    id 'io.spring.dependency-management' version '1.0.11.RELEASE'
    id 'java'
}

group = 'com.example'
version = '1.0.0-SNAPSHOT'
sourceCompatibility = '1.8'

repositories {
    mavenLocal() // 로컬 저장소
}

ext {
    querydslVersion = '4.4.0'
}

dependencies {
    // Spring Boot Web
    implementation 'org.springframework.boot:spring-boot-starter-web'

    // Spring Boot Data JPA
    implementation 'org.springframework.boot:spring-boot-starter-data-jpa'

    // Validation (JSR-303/JSR-380)
    implementation 'org.springframework.boot:spring-boot-starter-validation'

    // Logging (Default with Spring Boot)
    implementation 'org.springframework.boot:spring-boot-starter-logging'

    // Oracle JDBC Driver (ojdbc8)
    implementation 'com.oracle.database.jdbc:ojdbc8:19.8.0.0'

    // QueryDSL JPA
    implementation "com.querydsl:querydsl-jpa:${querydslVersion}"

    // QueryDSL APT for Code Generation
    compileOnly "com.querydsl:querydsl-apt:${querydslVersion}"
    annotationProcessor "com.querydsl:querydsl-apt:${querydslVersion}:jpa"

    // Springdoc OpenAPI UI
    implementation 'org.springdoc:springdoc-openapi-ui:1.6.9'

    // Springdoc OpenAPI Data REST
    implementation 'org.springdoc:springdoc-openapi-data-rest:1.6.9'

    // H2 Database (for testing only)
    testImplementation 'com.h2database:h2'
}

tasks.withType(JavaCompile) {
    options.encoding = 'UTF-8'
}
```
  
## 폐쇄망에서 Plugin 사용
 이클립스에서 필수적으로 사용되는 quick search 플러그인을 예시로 폐쇄망에서 Plugin을 사용하는 방법을 알아보자.
  
### 1. 외부망에서 플러그인 파일 다운로드
 아래 플러그인 파일을 다운받는다.
 [[org.springsource.ide.eclipse.commons.quicksearch_3.9.11.201912160745-RELEASE.jar]]
  
### 2. 이클립스 설치 경로에 파일 복사
 이클립스 설치 경로로 이동하면, plugins 폴더가 있다. 이 경로 하위에 quick search jar 파일을 이동시킨다.
  
### 3. 이클립스 설정 파일 수정
 끝으로 플러그인 정보가 들어있는 bundles.info 파일을 수정한다.
 
```
//<라이브러리 패키지명>,<버전>,<jar 경로>,4,false

org.springsource.ide.eclipse.commons.quicksearch,3.9.11.201912160745-RELEASE,file:/C:/Users/사용자이름/.p2/pool/plugins/org.springsource.ide.eclipse.commons.quicksearch_3.9.11.201912160745-RELEASE.jar,4,false
```
  
### 4. 이클립스 재시작
 끝으로 이클립스를 재시작하면 된다.
  
---
  
# 연결문서
- [eclipse-lombok](../../ide/ide-eclipse-lombok)