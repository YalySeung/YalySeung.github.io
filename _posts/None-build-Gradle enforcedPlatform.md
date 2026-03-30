---
title : "Gradle enforcedPlatform"
excerpt : "Gradle enforcedPlatform"
toc : true
toc_sticky : true
toc_label : "Gradle enforcedPlatform"
categories:
- Build
tags:
- [Gradle, DependencyManagement, Java, enforcedPlatform]
last_modified_at: NoneT08:00:00-10:00:00
---
  
---
  
## 개요

 `enforcedPlatform`은 Gradle에서 의존성 충돌을 방지하고 **특정 버전의 BOM(Bill of Materials)**을 강제로 적용할 때 사용하는 기능이다. 주로 여러 라이브러리 간 버전 불일치를 해결하기 위해 사용되며, Spring Boot, Cloud, AWS SDK 등의 BOM을 관리할 때 유용하다.

---
  
## 🧩 `platform` vs `enforcedPlatform`

| 항목    | platform          | enforcedPlatform    |
| ----- | ----------------- | ------------------- |
| 목적    | BOM에 명시된 버전 우선 적용 | BOM에 명시되지 않은 버전은 거부 |
| 적용 강도 | 느슨함               | 엄격함                 |
| 활용도   | 유연한 종속성 관리        | 종속성 통제를 엄격히 해야 할 때  |

---
  
## 📦 예제: Spring Boot BOM 적용
  
```kotlin
dependencies {
    implementation(enforcedPlatform("org.springframework.boot:spring-boot-dependencies:3.1.5"))
    implementation("org.springframework.boot:spring-boot-starter-web")
    implementation("org.springframework.boot:spring-boot-starter-data-jpa")
}
```

> **`enforcedPlatform`을 사용하면 하위 모듈이나 라이브러리에서 **명시적으로 다른 버전**을 선언하더라도 override 되지 않고 **build 에러가 발생**한다.**  
> 
{: .notice--info}  

---
  
## 💡 언제 사용하나?

- 기업 내 공통 BOM 강제 적용이 필요할 때
- 모듈 간 버전 충돌이 빈번하게 발생하는 프로젝트
- 외부 라이브러리들이 다양한 버전을 가져오는 경우 통제 목적

---
  
## ⚠️ 주의사항

- BOM 외 버전 사용 시 명확하게 예외 처리가 필요함
- 간혹 특정 라이브러리에서 BOM을 따르지 않거나 SNAPSHOT 버전을 사용할 경우 conflict 발생 가능

---
  
## 🔗 참고

- [Gradle Docs: platforms](https://docs.gradle.org/current/userguide/platforms.html)
- [Spring Boot Gradle Plugin Reference](https://docs.spring.io/spring-boot/docs/current/gradle-plugin/reference/htmlsingle/)

---
  
# 연결문서
- [Gradle](../../build/build-Gradle)
