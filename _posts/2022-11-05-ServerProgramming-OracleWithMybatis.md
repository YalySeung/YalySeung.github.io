---
title: "Oracle With Mybatis"
excerpt: "Spring MVC에 Mybatis 연동하기"

categories:
- ServerProgramming

tags:
- [ServerProgramming]

toc: true
toc_sticky: true
toc_label: "Oracle With Mybatis"

last_modified_at: 2022-11-06T08:00:00-10:00:00
---

# Mybatis
## 정의
  - JDBC를 이용한 퍼시스턴스 프레임워크

## 역할
  - JDBC를 이용한 커넥션 코드 및 변수 등 중복 작업을 대체
  - SQL, 동적 쿼리, 저장 프로시저, 고급 맵핑을 지원하는 SQL Mapper
  - SQL 쿼리를 XML 파일로 작성하여 프로그램 코드와 분리, 관리가 용이하다.

## 특징
  - Mybatis3과 Srping 연동 라이브러리로 제공됨
  - 스프링 bean 으로 등록하여 쉽게 사용 가능
  - Mybatis Mapper Interface를 통해 DB에 접근
  - 객체 프로퍼티로 파라미터와 결과 객체로 자동 매핑 지원
  - 스프링 연동 모듈 제공
  - 트랜잭션 관리 용이

# Gradle Dependency Setting
  ```xml

  dependencies {
    //Spring MVC
    testImplementation group: 'junit', name: 'junit', version: '4.11'
    implementation group: 'org.springframework', name: 'spring-context', version: '5.0.7.RELEASE'
    implementation group: 'org.springframework', name: 'spring-webmvc', version: '5.0.7.RELEASE'
    implementation group: 'org.springframework', name: 'spring-test', version: '5.0.7.RELEASE'
    implementation 'javax.servlet:servlet-api:2.5'

    //오라클, 마이바티스 연동
    implementation 'org.mybatis:mybatis-spring:2.0.7'
    implementation 'org.springframework:spring-jdbc:5.3.23'
    implementation 'commons-dbcp:commons-dbcp:1.4'
    implementation 'com.oracle.database.jdbc:ojdbc6:11.2.0.4'
  }

  ```

  수정 작업중입니다.................