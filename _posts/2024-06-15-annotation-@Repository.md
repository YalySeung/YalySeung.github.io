---
title : "@Repository"
excerpt : "@Repository"
toc : true
toc_sticky : true
toc_label : "@Repository"
categories:
- Annotation
tags:
- [Spring, JPA, Annotation]
last_modified_at: 2024-06-15T08:00:00-10:00:00
---
  
---
  
> **`@Repository`란?**  
>
>  Spring에서 **데이터 접근 계층(DAO: Data Access Object)**을 나타내는 어노테이션이다. 
{: .notice--info}  

  `@Repository`를 사용하면 **예외 처리를 자동으로 Spring의 데이터 예외 변환 기능과 통합할 수 있으며, 데이터 접근 계층을 명확히 구분할 수 있다.**
  
## 📌 사용법
  
### 1️⃣ `@Repository` 적용 예제
  
```java
import org.springframework.data.jpa.repository.JpaRepository;
import org.springframework.stereotype.Repository;

@Repository
public interface UserRepository extends JpaRepository<User, Long> {
    User findByEmail(String email);
}
```
  
## 📌 주요 기능
  
| 기능 | 설명 |
|------|------|
| `@Repository` | DAO 역할을 수행하는 클래스를 나타냄 |
| `JpaRepository<T, ID>` | 기본적인 CRUD 메서드를 제공 |
| `@Transactional(readOnly = true)` | 데이터 조회 작업 시 트랜잭션 적용 |
  
## 📌 커스텀 Repository 구현 예제
  
### 2️⃣ 사용자 정의 Repository 작성
  
```java
import org.springframework.data.jpa.repository.Query;
import org.springframework.data.repository.query.Param;

@Repository
public interface UserRepository extends JpaRepository<User, Long> {

    @Query("SELECT u FROM User u WHERE u.name = :name")
    User findByName(@Param("name") String name);
}
```
  
## 📌 `@Repository`의 장점과 단점
  
### ✅ 장점
- **Spring의 예외 변환(AOP 기반) 기능을 자동으로 제공**  
- DAO 계층을 명확히 구분할 수 있어 유지보수성이 높음  
- Spring Data JPA와 함께 사용하면 **자동으로 기본적인 CRUD 메서드 제공**  
  
### ❌ 단점
- **대규모 프로젝트에서 적절한 Repository 설계 없이 사용하면 유지보수 어려움**  
- **복잡한 쿼리는 Querydsl 등과 함께 사용해야 함**  

---
  
# 연결문서
- [JPA](../../jpa/jpa-JPA)
- [@Transactional](../../annotation/annotation-@Transactional)
