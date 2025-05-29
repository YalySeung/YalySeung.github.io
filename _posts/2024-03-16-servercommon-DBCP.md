---
title : "DBCP"
excerpt : "DBCP"
toc : true
toc_sticky : true
toc_label : "DBCP"
categories:
- ServerCommon
tags:
- [ServerCommon, Database]
last_modified_at: 2024-03-16T08:00:00-10:00:00
---
  
---
  
## 📌 DBCP란?

> **info**
>
> DBCP(Database Connection Pool)는 **데이터베이스 커넥션 객체를 미리 생성해 풀(Pool)에 저장해두고 재사용하는 방식**이다.  
> WAS가 DB에 접근할 때마다 Connection을 새로 생성하지 않고, 미리 준비된 Connection을 **필요할 때 가져다 쓰고 다시 반납**하는 구조다. 
{: .notice--info}  

---
  
## ✅ DBCP Workflow

1. 애플리케이션 구동 시 **미리 일정 수의 DB Connection 생성**
2. Connection은 **풀(Pool)**이라는 공간에 보관
3. 클라이언트 요청이 발생하면 Connection을 **풀에서 할당**
4. 작업 완료 후 Connection을 **반납**
5. 반납된 Connection은 **재사용되거나 만료되면 교체됨**

> **memo**
>
> Connection이 부족할 경우, **Client는 Connection이 생길 때까지 대기**하거나 **예외를 반환**하도록 설정할 수 있다. 
{: .notice--info}  

---
  
## ✅ DBCP의 장점

- **Connection 생성/소멸 비용 감소**
- **서버 자원 보호**: 최대 Connection 수 제한
- **응답 속도 향상**
- **자원 누수 방지**: 반납 누락 방지 기능 내장

---
  
## ✅ 주요 DBCP 구현체

| 라이브러리 | 설명 |
|------------|------|
| Apache Commons DBCP | 가장 널리 사용되는 Java 기반 커넥션 풀 |
| HikariCP | Spring Boot 기본 내장, 성능과 경량화에 강점 |
| C3P0 | 설정 유연성 좋으나 성능은 다소 낮음 |
| Tomcat JDBC | Tomcat 전용으로 최적화된 커넥션 풀 |

---
  
## ✅ 설정 예시 (Spring Boot + HikariCP)
  
```yaml
spring:
  datasource:
    url: jdbc:mysql://localhost:3306/mydb
    username: user
    password: pass
    driver-class-name: com.mysql.cj.jdbc.Driver
    hikari:
      maximum-pool-size: 10
      minimum-idle: 5
      idle-timeout: 30000
      max-lifetime: 600000
```

---
  
## ✅ 주의 사항

- 사용 후 반드시 **Connection close()** 호출 → 내부적으로 반환 처리
- **Connection leak 방지 설정** 필수 (`leakDetectionThreshold`)
- 최대 커넥션 수는 **DB 성능과 사용량 고려하여 설정**

---
  
# 연결문서
- [JDBC](../../servercommon/servercommon-JDBC)
