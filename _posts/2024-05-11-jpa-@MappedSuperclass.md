---
title : "@MappedSuperclass"
excerpt : "@MappedSuperclass"
toc : true
toc_sticky : true
toc_label : "@MappedSuperclass"
categories:
- JPA
tags:
- [Spring, JPA, Querydsl, Annotation]
last_modified_at: 2024-05-11T08:00:00-10:00:00
---
  
---
  
> **`@MappedSuperclass`란?**  
>
>  JPA에서 공통 필드를 가지지만 개별 테이블과 매핑되지 않는 **추상 클래스**에 사용하는 어노테이션이다. 
{: .notice--info}  

  `@MappedSuperclass`는 **ID가 없고 실제 테이블과 매핑이 필요 없는 Abstract Class**에 사용되며, 이를 상속하는 엔티티 클래스들이 공통 필드를 공유하도록 해준다.
  
## 사용법
  
### 1️⃣ `@MappedSuperclass` 적용 예제
  
```java
import javax.persistence.MappedSuperclass;
import javax.persistence.Column;
import java.time.LocalDateTime;

@MappedSuperclass
public abstract class BaseEntity {

    @Column(updatable = false)
    private LocalDateTime createdAt;

    private LocalDateTime updatedAt;
}
```
  
### 2️⃣ 상속하는 엔티티 클래스
  
```java
import javax.persistence.Entity;
import javax.persistence.GeneratedValue;
import javax.persistence.GenerationType;
import javax.persistence.Id;

@Entity
public class User extends BaseEntity {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;
}
```
  
## 장점과 단점
  
### ✅ 장점
- **공통 필드를 여러 엔티티에서 재사용 가능**  
- **코드 중복을 줄이고 유지보수성을 높일 수 있음**  
- **JPA Auditing과 결합하여 활용 가능**  
  
### ❌ 단점
- **직접 테이블과 매핑되지 않으며, 쿼리에서 직접 사용할 수 없음**  
- **복잡한 상속 구조에서는 `@Inheritance`를 고려해야 함**  

---
  
# 연결문서
- [JPA](../../jpa/jpa-JPA)
- [@Entity](../../jpa/jpa-@Entity)
- [@Inheritance](../../jpa/jpa-@Inheritance)
