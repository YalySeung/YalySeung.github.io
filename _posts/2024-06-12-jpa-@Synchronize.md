---
title : "@Synchronize"
excerpt : "@Synchronize"
toc : true
toc_sticky : true
toc_label : "@Synchronize"
categories:
- JPA
tags:
- [JPA, Spring]
last_modified_at: 2024-06-12T08:00:00-10:00:00
---
  
---
  
> **`@Synchronize`란?**  
>
>  Hibernate에서 네이티브 쿼리를 실행할 때 특정 엔티티와 동기화를 보장하기 위해 사용하는 어노테이션이다. 
{: .notice--info}  
  
## 주요 특징
- **네이티브 쿼리 실행 후 특정 엔티티와의 동기화 유지**  
- **JPA의 영속성 컨텍스트와 데이터베이스 간 불일치를 방지**  
- **Hibernate 전용 기능으로, JPA 표준이 아님**  
  
## 사용법
  
### 1️⃣ `@Synchronize` 적용 예제
  
```java
import org.hibernate.annotations.Synchronize;
import javax.persistence.*;

@NamedNativeQuery(
    name = "User.findActiveUsers",
    query = "SELECT * FROM user WHERE status = 'ACTIVE'",
    resultClass = User.class
)
@Synchronize("user")
@Entity
public class User {
    
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    
    private String name;
    private String status;
}
```
  
### 2️⃣ `@Synchronize`가 필요한 이유
- 네이티브 쿼리를 실행하면 JPA의 영속성 컨텍스트가 변경 사항을 인식하지 못할 수 있음  
- `@Synchronize`를 사용하면 **해당 엔티티를 자동으로 동기화하여 최신 상태 유지 가능**  
  
## 장점과 단점
  
### ✅ 장점
- **네이티브 쿼리와 JPA 엔티티의 데이터 정합성 유지 가능**  
- **JPA 캐시를 최신 상태로 유지하여 일관된 데이터 제공**  
  
### ❌ 단점
- **Hibernate 전용 기능이므로 JPA 표준이 아님**  
- **사용하지 않아도 플러시(Flush)를 수동으로 수행하면 해결 가능**  

---
  
# 연결문서
- [JPA](../../jpa/jpa-JPA)
- [Hibernate](../../jpa/jpa-Hibernate)
