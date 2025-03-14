---
title : "@CreatedDate"
excerpt : "@CreatedDate"
toc : true
toc_sticky : true
toc_label : "@CreatedDate"
categories:
- JPA
tags:
- [Spring, JPA]
last_modified_at: 2024-05-29T08:00:00-10:00:00
---
  
---
  
> **`@CreatedDate`란?**  
>
>  엔티티가 생성될 때 자동으로 등록 시간을 저장하는 JPA Auditing 어노테이션이다. 
{: .notice--info}  

  서비스를 구현할 때, 계정의 **등록 시간**과 같은 데이터는 생성 시점에 현재 시간을 Database에 Insert 해야 한다.  
  `@CreatedDate` 어노테이션은 **생성 날짜를 기본값으로 자동 맵핑해주는 어노테이션**으로 필요한 Entity Field에 설정하면 된다.
  
## 사용법
  
### 1️⃣ `@CreatedDate` 적용 예제
  
```java
@CreatedDate  
@Column(name = "REG_DT", nullable = false)  
@Convert(converter = DateConverter.class)  
private DateTime registDateTime;
```
  
### 2️⃣ JPA Auditing과 함께 사용
  
```java
import org.springframework.data.annotation.CreatedDate;
import org.springframework.data.jpa.domain.support.AuditingEntityListener;

import javax.persistence.*;
import java.time.LocalDateTime;

@MappedSuperclass
@EntityListeners(AuditingEntityListener.class)
public abstract class BaseEntity {

    @CreatedDate
    @Column(updatable = false)
    private LocalDateTime createdDate;
}
```

  이 클래스를 상속하면 모든 엔티티에서 생성 시간을 자동으로 기록할 수 있다.

---
  
# 연결문서
- [JPA](../../jpa/jpa-JPA)
- [@EnableJpaAuditing](../../jpa/jpa-@EnableJpaAuditing)
