---
title : "CustomRepository"
excerpt : "CustomRepository"
toc : true
toc_sticky : true
toc_label : "CustomRepository"
categories:
- JPA
tags:
- [Spring, JPA, Repository]
last_modified_at: 2024-06-15T08:00:00-10:00:00
---
  
---
  
> **Custom Repository란?**  
>
>  JPA의 기본 제공 기능 외에 **사용자 정의 쿼리 및 비즈니스 로직을 추가하기 위한 Repository 확장 방식**이다. 
{: .notice--info}  

  기본적인 CRUD 기능은 `JpaRepository`가 제공하지만, **복잡한 쿼리나 특정 로직이 필요한 경우 Custom Repository를 구현하여 확장할 수 있다.**  
  
## 📌 Custom Repository 구현 방법
  
### 1️⃣ 인터페이스 정의 (Custom Repository 인터페이스 생성)
  
```java
public interface CustomUserRepository {
    List<User> findActiveUsers();
}
```
  
### 2️⃣ 구현 클래스 작성 (`CustomUserRepositoryImpl`)
  
```java
import com.querydsl.jpa.impl.JPAQueryFactory;
import org.springframework.stereotype.Repository;
import java.util.List;
import static com.example.domain.QUser.user;

@Repository
public class CustomUserRepositoryImpl implements CustomUserRepository {

    private final JPAQueryFactory queryFactory;

    public CustomUserRepositoryImpl(JPAQueryFactory queryFactory) {
        this.queryFactory = queryFactory;
    }

    @Override
    public List<User> findActiveUsers() {
        return queryFactory.selectFrom(user)
                .where(user.isActive.eq(true))
                .fetch();
    }
}
```
  
### 3️⃣ `JpaRepository`와 Custom Repository 통합
  
```java
public interface UserRepository extends JpaRepository<User, Long>, CustomUserRepository {
}
```
  
## 📌 Custom Repository를 활용하는 이유
  
| 기능 | 설명 |
|------|------|
| 복잡한 쿼리 | Querydsl, JPQL을 활용한 동적 쿼리 작성 |
| 성능 최적화 | 네이티브 쿼리 또는 Batch Query 적용 |
| 비즈니스 로직 분리 | Service Layer의 코드 간결화 |
  
## 📌 장점과 단점
  
### ✅ 장점
- 기본 `JpaRepository` 기능을 유지하면서 확장 가능  
- Querydsl, JPQL을 활용하여 복잡한 쿼리를 효율적으로 관리  
- **비즈니스 로직과 데이터 접근 로직을 분리**하여 유지보수성 향상  
  
### ❌ 단점
- Custom Repository 구현 시 추가적인 코드 작성 필요  
- Querydsl, JPQL 사용 시 학습 곡선이 존재  

---
  
# 연결문서
- [@Repository](../../annotation/annotation-@Repository)
- [Spring Data JPA](../../jpa/jpa-Spring-Data-JPA)
