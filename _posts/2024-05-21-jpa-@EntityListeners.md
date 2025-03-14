---
title : "@EntityListeners"
excerpt : "@EntityListeners"
toc : true
toc_sticky : true
toc_label : "@EntityListeners"
categories:
- JPA
tags:
- [Spring, Querydsl, JPA]
last_modified_at: 2024-05-21T08:00:00-10:00:00
---
  
---
  
> **`@EntityListeners`란?**  
>
>  Entity Lifecycle의 특정 시점에 호출할 수 있는 콜백을 제공하는 어노테이션이다. 
{: .notice--info}  

  `@EntityListeners`를 사용하면 **JPA 엔티티의 생명주기 이벤트에 대한 특정 동작을 정의할 수 있다.**
  
## 주요 콜백 메서드
  
| Callback Option | 호출 시점      |
| --------------- | --------- |
| @PrePersist     | 영속화 직전    |
| @PostPersist    | 영속화 후     |
| @PostLoad       | 로드 이후     |
| @PreUpdate      | update 이전 |
| @PostUpdate     | update 이후 |
| @PreRemove      | delete 이전 |
| @PostRemove     | delete 이후 |
  
## 사용법
  
### 1️⃣ `@EntityListeners` 적용 예제
  
```java
import javax.persistence.*;

@Entity
@EntityListeners(AuditListener.class)
public class User {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;
}
```
  
### 2️⃣ Listener 클래스 구현
  
```java
import javax.persistence.*;

public class AuditListener {

    @PrePersist
    public void beforeSave(Object obj) {
        System.out.println("객체가 저장되기 전: " + obj);
    }

    @PostPersist
    public void afterSave(Object obj) {
        System.out.println("객체가 저장된 후: " + obj);
    }
}
```
  
## 장점과 단점
  
### ✅ 장점
- **엔티티의 생명주기 이벤트에 대해 세밀한 제어 가능**  
- **로깅, 감사(Audit) 기능 구현에 유용**  
  
### ❌ 단점
- **비즈니스 로직과 분리되지 않으면 코드가 복잡해질 수 있음**  
- **동작 방식이 데이터베이스 트리거와 유사하여 성능 고려 필요**  

---
  
# 연결문서
