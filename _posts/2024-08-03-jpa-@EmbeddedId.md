---
title : "@EmbeddedId"
excerpt : "@EmbeddedId"
toc : true
toc_sticky : true
toc_label : "@EmbeddedId"
categories:
- JPA
tags:
- [Spring, Annotation]
last_modified_at: 2024-08-03T08:00:00-10:00:00
---
  
---
  
> **`@EmbeddedId`란?**  
>
>  JPA에서 복합 키(Composite Key)를 정의할 때 사용하는 어노테이션으로, `@Embeddable` 클래스를 활용하여 복합 키를 정의할 수 있다. 
{: .notice--info}  
  
## Gradle 설정
 JPA를 사용하기 위해 `spring-boot-starter-data-jpa` 의존성을 추가해야 한다.
  
```groovy
dependencies {
    implementation 'org.springframework.boot:spring-boot-starter-data-jpa'
    implementation 'org.hibernate:hibernate-core:5.6.9.Final'
}
```
  
## 역할
- **JPA에서 복합 키를 설정할 때 사용**  
- **`@Embeddable` 클래스와 함께 사용하여 객체로 키를 관리 가능**  
- **기본 키를 여러 개 결합하여 하나의 키로 관리**  
  
## 사용법
  
### 1️⃣ `@Embeddable` 클래스로 복합 키 정의
  
```java
import java.io.Serializable;
import javax.persistence.Embeddable;

@Embeddable
public class OrderKey implements Serializable {
    private Long orderId;
    private Long productId;

    // 기본 생성자, equals(), hashCode() 필수 구현
}
```
  
### 2️⃣ `@EmbeddedId`로 복합 키 사용
  
```java
import javax.persistence.*;

@Entity
public class Order {
    
    @EmbeddedId
    private OrderKey id;

    private String orderStatus;
}
```

---
  
# 연결문서
- [@Embeddable](../../jpa/jpa-@Embeddable)
