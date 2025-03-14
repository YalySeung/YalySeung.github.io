---
title : "@GenericGenerator"
excerpt : "@GenericGenerator"
toc : true
toc_sticky : true
toc_label : "@GenericGenerator"
categories:
- JPA
tags:
- [JPA, Annotation]
last_modified_at: 2024-12-04T08:00:00-10:00:00
---
  
---
  
> **`@GenericGenerator`란?**  
>
>  Hibernate에서 사용자 지정 식별자 생성 전략을 정의할 때 사용하는 어노테이션이다. 
{: .notice--info}  

  Oracle DB에서 **시퀀스를 사용하여 테이블의 PK를 생성하고, 이를 `String` 타입으로 변환해야 하는 경우**가 있다.  
  기본적으로 JPA의 `@GeneratedValue`는 숫자 타입에 적합하지만, `@GenericGenerator`를 사용하면 **String 타입의 PK 생성이 가능하다.**
  
## 해결 방법
  
### 1️⃣ `@PrePersist`를 활용한 방식
  `@PrePersist`를 사용하면 **영속화 전 시점에서 String 변환 작업을 수행**할 수 있다.
  
```java
@Entity
public class Role {
    @Id
    private String id;

    @PrePersist
    public void prePersist() {
        this.id = String.valueOf(this.id);
    }
}
```
  
### 2️⃣ `@GenericGenerator`를 활용한 방식 (권장)
  `@GenericGenerator`를 사용하면 **커스텀 식별자 생성 전략을 설정하여 String 타입의 PK를 자동으로 생성**할 수 있다.
  
#### 2-1. `IdentifierGenerator` 구현
  
```java
public class StringSequenceIdentifierGenerator implements IdentifierGenerator {
    @Override
    public Serializable generate(SharedSessionContractImplementor session, Object object) {
        String sql = "SELECT my_sequence.NEXTVAL FROM DUAL";
        Long seqValue = ((Number) session.createNativeQuery(sql).getSingleResult()).longValue();
        return String.valueOf(seqValue);
    }
}
```
  
#### 2-2. 엔티티에 `@GenericGenerator` 적용
  
```java
@Entity
public class Role {
    @Id
    @Column(name = "ROLE_PK")
    @GeneratedValue(generator = "role_seq_gen")
    @GenericGenerator(name = "role_seq_gen", strategy = "com.example.StringSequenceIdentifierGenerator")
    private String pk;
}
```
  
## 장점과 단점
  
### ✅ 장점
- **Oracle DB의 시퀀스를 활용하여 String 타입 PK를 자동 생성 가능**  
- **JPA 기본 제공 방식(`@GeneratedValue`)으로 해결할 수 없는 문제 해결**  
- **식별자 생성 전략을 커스텀할 수 있어 확장성이 높음**  
  
### ❌ 단점
- **Hibernate 전용 기능으로 JPA 표준이 아님**  
- **별도의 식별자 생성 클래스를 작성해야 하는 추가 작업 필요**  

---
  
# 연결문서
- [@Convert](../../jpa/jpa-@Convert)
- [@GeneratedValue](../../jpa/jpa-@GeneratedValue)
- [@PrePersist](../../jpa/jpa-@PrePersist)
