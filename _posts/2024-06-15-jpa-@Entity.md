---
title : "@Entity"
excerpt : "@Entity"
toc : true
toc_sticky : true
toc_label : "@Entity"
categories:
- JPA
tags:
- [JPA, Spring, Querydsl]
last_modified_at: 2024-06-15T08:00:00-10:00:00
---
  
---
  
> **`@Entity`란?**  
>
>  JPA(Java Persistence API)에서 **데이터베이스 테이블과 매핑되는 클래스**를 정의하는 어노테이션이다. 
{: .notice--info}  

  `@Entity`를 선언하면 **클래스가 JPA 엔티티로 인식되며, 데이터베이스 테이블과 연결된다.**  
  테이블과 매핑할 클래스는 **반드시 기본 생성자가 있어야 하며**, `@Id`를 포함한 **기본 키가 필요**하다.
  
## 📌 사용법
  
### 1️⃣ `@Entity` 적용 예제
  
```java
import javax.persistence.*;

@Entity
@Table(name = "users") // 테이블 이름 명시 (생략 가능)
public class User {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY) // 자동 증가 ID 설정
    private Long id;

    @Column(name = "username", nullable = false, length = 50) // 컬럼 속성 지정
    private String name;

    protected User() {} // 기본 생성자 (JPA에서 필수)

    public User(String name) {
        this.name = name;
    }
}
```
  
## 📌 주요 어노테이션
  
| 어노테이션 | 설명 |
|-----------|------|
| `@Entity` | JPA 엔티티 클래스 선언 |
| `@Table(name = "테이블명")` | 매핑할 데이터베이스 테이블 이름 지정 |
| `@Id` | 기본 키(PK) 필드 지정 |
| `@GeneratedValue(strategy = …)` | 기본 키 자동 생성 전략 설정 |
| `@Column(name = "컬럼명", nullable = …, length = …)` | 컬럼 매핑 세부 설정 |
  
## 📌 `@Entity`와 테이블 매핑 시 주의할 점
- 클래스에는 `@Entity` 선언 필수  
- **기본 키(PK)는 반드시 지정** (`@Id` 사용)  
- 기본 생성자 **반드시 필요** (`protected` or `public` 사용)  
- JPA는 `final` 클래스 또는 `final` 필드를 지원하지 않음  
  
## 📌 장점과 단점
  
### ✅ 장점
- **객체와 관계형 데이터베이스 간 매핑을 자동으로 수행**  
- **SQL을 직접 작성하지 않아도 데이터 조작 가능**  
- **JPA의 다른 기능(`@ManyToOne`, `@OneToMany` 등)과 쉽게 연동 가능**  
  
### ❌ 단점
- **매핑 오류 발생 시 런타임까지 알기 어려움**  
- **SQL보다 학습 난이도가 높을 수 있음**  

> **info**
>
> Controller Request 데이터로 Entity를 사용하면 유지보수하기 어렵고, 때로는 테이블 구조가 노출 될 수 있으므로 지양하자. 
{: .notice--info}  

---
  
# 연결문서
- [JPA](../../jpa/jpa-JPA)
- [@Table](../../annotation/annotation-@Table)
- [@Column](../../jpa/jpa-@Column)
