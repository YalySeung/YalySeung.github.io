---
title : "@ColumnDefault"
excerpt : "@ColumnDefault"
toc : true
toc_sticky : true
toc_label : "@ColumnDefault"
categories:
- JPA
tags:
- [Spring, JPA, Querydsl]
last_modified_at: 2024-05-20T08:00:00-10:00:00
---
  
---
  
> **`@ColumnDefault`란?**  
>
>  Hibernate에서 제공하는 어노테이션으로, 특정 컬럼의 기본값을 설정하는 데 사용된다. 
{: .notice--info}  
  
## 주요 특징
- **Hibernate 전용 어노테이션으로 JPA 표준이 아님**  
- **컬럼의 기본값을 설정하여 NULL 값 방지**  
- **SQL `DEFAULT` 값을 설정하는 방식과 동일**  
  
## 사용법
  
### 1️⃣ `@ColumnDefault` 적용 예제
  
```java
import org.hibernate.annotations.ColumnDefault;
import javax.persistence.Column;
import javax.persistence.Entity;
import javax.persistence.GeneratedValue;
import javax.persistence.GenerationType;
import javax.persistence.Id;

@Entity
public class User {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @ColumnDefault("'ACTIVE'")
    @Column(nullable = false)
    private String status;
}
```
  
### 2️⃣ SQL 기본값 설정과 비교
  
| 방법 | 설명 | 적용 대상 |
|------|------|------|
| `@ColumnDefault` | Hibernate 어노테이션 사용 | JPA 엔티티 |
| `DEFAULT` | SQL 스키마에서 기본값 설정 | 데이터베이스 테이블 |
  
## 장점과 단점
  
### ✅ 장점
- **기본값을 코드에서 명시적으로 설정 가능**  
- **엔티티 레벨에서 기본값을 관리하여 유지보수 용이**  
  
### ❌ 단점
- **JPA 표준이 아니라 Hibernate에 종속됨**  
- **DBMS에 따라 작동 방식이 다를 수 있음**  

---
  
# 연결문서
- [JPA](../../jpa/jpa-JPA)
- [Hibernate](../../jpa/jpa-Hibernate)
