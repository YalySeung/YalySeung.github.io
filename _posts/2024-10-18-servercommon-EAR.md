---
title : "EAR"
excerpt : "EAR"
toc : true
toc_sticky : true
toc_label : "EAR"
categories:
- ServerCommon
tags:
- [ServerCommon]
last_modified_at: 2024-10-18T08:00:00-10:00:00
---
  
---
  
> **EAR 이란?**  
>
> Enterprise Archive 의 약어로 하나 이상의 모듈들을 하나의 아카이브로 묶어서 여러 모듈이 애플리케이션 서버에 동시에 일관성 있게 배치될 수 있도록 하기 위한 자바 EE에 쓰이는 파일 형식을 의미한다. 
{: .notice--info}  
  
## EAR의 주요 특징
- **JAR 및 WAR 파일을 포함하여 여러 모듈을 통합 관리**  
- **Java EE 환경에서 배포의 일관성을 유지**할 수 있도록 설계됨
- **애플리케이션 서버(WebLogic, JBoss, WildFly 등)에서 사용됨**  
- **EJB 모듈, 웹 애플리케이션 모듈, 라이브러리 모듈을 하나의 패키지로 배포 가능**  
  
## EAR 파일 구조
 EAR 파일 내부는 여러 모듈이 포함된 구조를 가진다.
  
```plaintext
myapp.ear
 ├── META-INF/application.xml
 ├── myapp-ejb.jar   # EJB 모듈
 ├── myapp-web.war   # 웹 애플리케이션 모듈
 ├── lib/
 │   ├── shared-library.jar
 │   ├── utility.jar
```
  
## EAR과 다른 Java 배포 파일 비교
  
| 배포 파일 | 설명 | 주요 사용처 |
|------|---------|---------|
| EAR | 여러 모듈을 하나의 패키지로 배포 | 엔터프라이즈 애플리케이션 |
| WAR | 웹 애플리케이션 배포 | 웹 서버 및 WAS |
| JAR | Java 라이브러리 및 실행 가능 파일 | 독립 실행형 애플리케이션 |
  
## EAR의 장점과 단점
  
### ✅ 장점
- 모든 모듈을 하나의 배포 단위로 묶어 **일관된 배포 가능**  
- 여러 모듈이 포함되어 **의존성 관리가 용이**  
- 대규모 엔터프라이즈 애플리케이션 개발에 적합  
  
### ❌ 단점
- **구성이 복잡하고, 배포 과정이 무거울 수 있음**
- 단일 모듈(WAR, JAR)보다 배포 속도가 느릴 수 있음  

---
  
# 연결문서
- [JAR](../../java/java-JAR)
