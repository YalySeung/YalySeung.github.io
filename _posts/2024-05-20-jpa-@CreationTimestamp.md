---
title : "@CreationTimestamp"
excerpt : "@CreationTimestamp"
toc : true
toc_sticky : true
toc_label : "@CreationTimestamp"
categories:
- JPA
tags:
- [Spring, JPA, Querydsl]
last_modified_at: 2024-05-20T08:00:00-10:00:00
---
  
---
  
> **`@CreationTimestamp`란?**  
>
>  Hibernate에서 제공하는 어노테이션으로, 엔티티가 생성될 때 자동으로 생성 시간을 저장한다. 
{: .notice--info}  
  
## 주요 특징
- **JPA의 `@CreatedDate`와 유사하지만 Hibernate 전용 기능**  
- **엔티티가 생성될 때 자동으로 Timestamp 저장**  
- **SQL `CURRENT_TIMESTAMP` 값을 사용하여 DB에서 직접 시간 설정**  
  
## 사용법
  
### 1️⃣ `@CreationTimestamp` 적용 예제
  
```java
import org.hibernate.annotations.CreationTimestamp;
import javax.persistence.Column;
import javax.persistence.Entity;
import javax.persistence.GeneratedValue;
import javax.persistence.GenerationType;
import javax.persistence.Id;
import java.time.LocalDateTime;

@Entity
public class User {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @CreationTimestamp
    @Column(updatable = false, nullable = false)
    private LocalDateTime createdAt;
}
```
  
### 2️⃣ `@CreatedDate`와 비교
  
| 어노테이션 | 제공 프레임워크 | 작동 방식 | 적용 방식 |
|------------|--------------|-----------|-----------|
| `@CreatedDate` | Spring Data JPA | 애플리케이션 코드에서 시간 관리 | `@EnableJpaAuditing` 필요 |
| `@CreationTimestamp` | Hibernate | DB `CURRENT_TIMESTAMP` 사용 | 별도 설정 필요 없음 |
  
## 장점과 단점
  
### ✅ 장점
- **데이터베이스에서 직접 `CURRENT_TIMESTAMP` 값을 설정**  
- **애플리케이션 코드 수정 없이 자동 시간 저장 가능**  
  
### ❌ 단점
- **JPA 표준이 아닌 Hibernate 전용 기능**  
- **DB에서 시간 관리하므로 테스트 환경에 따라 결과가 달라질 수 있음**  

---
  
# 연결문서
- [@CreatedDate](../../jpa/jpa-@CreatedDate)
- [JPA](../../jpa/jpa-JPA)
