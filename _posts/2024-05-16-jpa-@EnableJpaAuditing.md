---
title : "@EnableJpaAuditing"
excerpt : "@EnableJpaAuditing"
toc : true
toc_sticky : true
toc_label : "@EnableJpaAuditing"
categories:
- JPA
tags:
- [Spring, Annotation, JPA]
last_modified_at: 2024-05-16T08:00:00-10:00:00
---
  
---
  
> **Auditing 이란?**  
>
>  사전적 의미로 감사, 심사 등의 의미를 가지고 있다. Spring Data JPA에서는 Entity의 생성, 변경을 감지하여 정보를 기록하는 것을 의미한다. 
{: .notice--info}  
  
## Gradle 설정
  JPA Auditing 기능을 사용하려면 `spring-boot-starter-data-jpa` 의존성을 추가해야 한다.
  
```groovy
dependencies {
    implementation 'org.springframework.boot:spring-boot-starter-data-jpa'
}
```
  
## 역할
- **Entity의 생성 및 변경 이력을 자동으로 기록**  
- **`@CreatedDate`, `@LastModifiedDate` 등을 활용하여 생성 및 수정 시간 자동 저장**  
- **`@CreatedBy`, `@LastModifiedBy`와 함께 사용하면 생성자 및 수정자 정보 저장 가능**  
  
## 사용법
  
### 1️⃣ `@EnableJpaAuditing` 설정
  `@EnableJpaAuditing`을 활성화하여 JPA Auditing 기능을 사용할 수 있다.
  
```java
@Configuration
@EnableJpaAuditing
public class JpaConfig {
}
```
  
### 2️⃣ Auditing 기능을 포함한 엔티티 정의
  
```java
import org.springframework.data.annotation.CreatedDate;
import org.springframework.data.annotation.LastModifiedDate;
import org.springframework.data.jpa.domain.support.AuditingEntityListener;

import javax.persistence.*;
import java.time.LocalDateTime;

@MappedSuperclass
@EntityListeners(AuditingEntityListener.class)
public abstract class BaseEntity {

    @CreatedDate
    @Column(updatable = false)
    private LocalDateTime createdDate;

    @LastModifiedDate
    private LocalDateTime modifiedDate;
}
```

  이 클래스를 상속하면 모든 엔티티에서 생성 및 수정 시간을 자동으로 기록할 수 있다.

---
  
# 연결문서
- [JPA](../../jpa/jpa-JPA)
