---
title : "@DynamicUpdate"
excerpt : "@DynamicUpdate"
toc : true
toc_sticky : true
toc_label : "@DynamicUpdate"
categories:
- Annotation
tags:
- [Spring, Annotation]
last_modified_at: 2024-04-07T08:00:00-10:00:00
---
  
---
  
> **`@DynamicUpdate`란?**  
>
>  JPA 엔티티 변경 시 변경된 필드만 업데이트하는 Hibernate 어노테이션이다. 
{: .notice--info}  
  
## Artifact
  `@DynamicUpdate`을 사용하려면 Hibernate가 포함된 JPA 환경에서 동작해야 한다.
  
```groovy
dependencies {
    implementation 'org.springframework.boot:spring-boot-starter-data-jpa'
    implementation 'org.hibernate:hibernate-core:5.6.9.Final'
}
```
  
## 역할
- **JPA 엔티티에서 변경된 필드만 업데이트하도록 최적화**  
- **불필요한 업데이트 SQL을 방지하여 성능 개선**  
- **Hibernate의 변경 감지(Dirty Checking) 메커니즘과 함께 사용됨**  
  
## 사용법
  
### 1️⃣ `@DynamicUpdate` 적용 예제
  
```java
import org.hibernate.annotations.DynamicUpdate;
import javax.persistence.*;

@Entity
@DynamicUpdate
public class User {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;

    private String email;
}
```
  
### 2️⃣ 일반적인 JPA 업데이트와 비교
  
| 방식 | 설명 | 실행되는 SQL |
|------|------|-------------|
| 기본 JPA 업데이트 | 변경되지 않은 필드도 함께 업데이트됨 | `UPDATE user SET name=?, email=? WHERE id=?` |
| `@DynamicUpdate` 사용 | 변경된 필드만 업데이트됨 | `UPDATE user SET email=? WHERE id=?` |
  
## 장점과 단점
  
### ✅ 장점
- **변경된 필드만 업데이트하여 불필요한 SQL 실행 방지**  
- **트랜잭션 내에서 성능 최적화 가능**  
  
### ❌ 단점
- **쿼리 캐싱이 어렵고, 매번 업데이트할 필드를 동적으로 결정해야 함**  
- **Hibernate에 의존적이며, JPA 표준이 아님**  

---
  
# 연결문서
- [JPA Dirty Checking](../../jpa/jpa-JPA-Dirty-Checking)
- [@Entity](../../jpa/jpa-@Entity)
