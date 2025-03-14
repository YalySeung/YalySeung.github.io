---
title : "@EnableTransactionManagement"
excerpt : "@EnableTransactionManagement"
toc : true
toc_sticky : true
toc_label : "@EnableTransactionManagement"
categories:
- JPA
tags:
- [Spring, Annotation, JPA]
last_modified_at: 2024-04-21T08:00:00-10:00:00
---
  
---
  
> **`@EnableTransactionManagement`란?**  
>
>  Spring에서 선언적 트랜잭션 관리를 활성화하는 어노테이션이다. 
{: .notice--info}  
  
## Artifact
  `@EnableTransactionManagement`을 사용하려면 Spring의 트랜잭션 관련 의존성을 추가해야 한다.
  
```groovy
dependencies {
    implementation 'org.springframework.boot:spring-boot-starter-data-jpa'
}
```
  
## 역할
- **Spring의 트랜잭션 관리를 활성화**  
- **`@Transactional` 어노테이션을 사용하여 트랜잭션을 자동 처리 가능**  
- **JPA, JDBC, MyBatis 등 다양한 데이터 접근 기술과 함께 사용 가능**  
  
## 사용법
  
### 1️⃣ 기본 설정
  
```java
import org.springframework.context.annotation.Configuration;
import org.springframework.transaction.annotation.EnableTransactionManagement;

@Configuration
@EnableTransactionManagement
public class TransactionConfig {
}
```
  
### 2️⃣ `@Transactional`과 함께 사용
  
```java
import org.springframework.stereotype.Service;
import org.springframework.transaction.annotation.Transactional;

@Service
public class UserService {

    @Transactional
    public void createUser(User user) {
        // 데이터베이스 트랜잭션 내에서 실행됨
    }
}
```

---
  
# 연결문서
- [@Transactional](../../annotation/annotation-@Transactional)
- [JPA](../../jpa/jpa-JPA)
