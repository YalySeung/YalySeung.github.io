---
title : "@Modifying"
excerpt : "@Modifying"
toc : true
toc_sticky : true
toc_label : "@Modifying"
categories:
- Annotation
tags:
- [Spring, Annotation]
last_modified_at: 2024-04-09T08:00:00-10:00:00
---
  
---
  
> **`@Modifying`이란?**  
>
>  Spring Data JPA에서 `@Query`를 사용할 때 데이터 변경(UPDATE, DELETE)을 수행하도록 지정하는 어노테이션이다. 
{: .notice--info}  
  
## Artifact
  `@Modifying`을 사용하려면 Spring Data JPA 의존성을 추가해야 한다.
  
```groovy
dependencies {
    implementation 'org.springframework.boot:spring-boot-starter-data-jpa'
}
```
  
## 역할
- Spring Data JPA에서 `@Query`를 사용한 UPDATE 및 DELETE 실행 가능
- 변경된 데이터를 반영하기 위해 **`@Transactional`과 함께 사용**  
- **자동으로 플러시(`flush`)를 수행**하여 변경 사항을 DB에 적용
  
## 사용법
  
### 1️⃣ `@Modifying` 적용 예제
  
```java
import org.springframework.data.jpa.repository.Modifying;
import org.springframework.data.jpa.repository.Query;
import org.springframework.transaction.annotation.Transactional;

public interface UserRepository extends JpaRepository<User, Long> {

    @Modifying
    @Transactional
    @Query("UPDATE User u SET u.status = 'INACTIVE' WHERE u.id = :id")
    int deactivateUser(Long id);
}
```
  
### 2️⃣ `@Transactional`과 함께 사용해야 하는 이유
- `@Modifying`을 사용할 때는 **트랜잭션을 관리하기 위해 `@Transactional`이 필요**  
- 데이터 변경 작업이므로 **자동으로 flush가 수행됨**  
- `clearAutomatically = true` 옵션을 사용하면 **자동으로 영속성 컨텍스트를 초기화하여 최신 데이터 유지 가능**
  
```java
@Modifying(clearAutomatically = true)
@Query("DELETE FROM User u WHERE u.status = 'INACTIVE'")
void deleteInactiveUsers();
```

---
  
# 연결문서
- [JPA](../../jpa/jpa-JPA)
- [@Query](../../jpa/jpa-@Query)
- [@Transactional](../../annotation/annotation-@Transactional)
