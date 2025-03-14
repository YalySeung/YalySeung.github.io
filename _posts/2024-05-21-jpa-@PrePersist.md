---
title : "@PrePersist"
excerpt : "@PrePersist"
toc : true
toc_sticky : true
toc_label : "@PrePersist"
categories:
- JPA
tags:
- [JPA, Spring, Querydsl]
last_modified_at: 2024-05-21T08:00:00-10:00:00
---
  
---
  
> **`@PrePersist`란?**  
>
>  JPA 엔티티의 **영속화 직전에 실행되는 콜백 메서드**를 정의할 수 있도록 지원하는 어노테이션이다. 
{: .notice--info}  

  `@PrePersist`를 사용하면 **데이터가 저장되기 직전에 특정 로직을 실행할 수 있으며, 생성일 자동 설정 등의 용도로 활용될 수 있다.**
  
## 사용법
  
### 1️⃣ `@PrePersist` 적용 예제
  
```java
import javax.persistence.*;

@Entity  
@Table(name = "COM_VAR")  
public class CommonVariable {  

    private String variableValue;

    public CommonVariable(CommonVariable commonVariable) {  
        this.variableValue = commonVariable.variableValue;  
    }  

    @PrePersist  
    public void beforeSave() {  
        System.out.println(variableValue);
    }
}
```
  
### 2️⃣ 엔티티 리스너와 함께 사용
  
```java
import javax.persistence.*;

public class AuditListener {

    @PrePersist
    public void beforeInsert(Object obj) {
        System.out.println("객체가 저장되기 전 실행: " + obj);
    }
}
```
  
```java
@Entity
@EntityListeners(AuditListener.class)
public class User {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;
}
```
  
## 장점과 단점
  
### ✅ 장점
- **엔티티 저장 직전에 특정 로직 실행 가능**  
- **생성일 자동 등록, 기본값 설정 등에 유용**  
  
### ❌ 단점
- **비즈니스 로직이 엔티티 내부에 포함될 경우 유지보수가 어려워질 수 있음**  
- **복잡한 로직을 처리하기에는 한계가 있음**  

---
  
# 연결문서
