---
title : "@Table"
excerpt : "@Table"
toc : true
toc_sticky : true
toc_label : "@Table"
categories:
- Annotation
tags:
- [JPA, Spring]
last_modified_at: 2024-06-15T08:00:00-10:00:00
---
  
---
  
> **`@Table`이란?**  
>
>  JPA에서 엔티티 클래스가 매핑될 데이터베이스 테이블의 이름과 속성을 지정하는 어노테이션이다. 
{: .notice--info}  

  `@Table` 어노테이션을 사용하면 **테이블 이름을 명시적으로 지정하고, 인덱스 및 유니크 제약 조건을 설정할 수 있다.**  
  
## 📌 사용법
  
### 1️⃣ 기본적인 `@Table` 적용 예제
  
```java
import javax.persistence.*;

@Entity
@Table(name = "users") // 테이블 이름을 "users"로 지정
public class User {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @Column(name = "username", nullable = false, length = 50)
    private String name;

    protected User() {} // JPA에서 기본 생성자 필수

    public User(String name) {
        this.name = name;
    }
}
```
  
## 📌 `@Table` 속성 정리
  
| 속성           | 설명 |
|--------------|------|
| `name`       | 매핑할 테이블의 이름을 지정 |
| `schema`     | 매핑할 데이터베이스의 스키마 지정 (기본값: DB 기본 스키마) |
| `catalog`    | 매핑할 카탈로그 지정 |
| `indexes`    | 테이블 인덱스를 설정 |
| `uniqueConstraints` | 유니크 제약 조건을 설정 |
  
## 📌 인덱스 및 유니크 키 설정
  
### 2️⃣ `@Index`와 `@UniqueConstraint` 활용 예제
  
```java
import javax.persistence.*;

@Entity
@Table(
    name = "users",
    indexes = {@Index(name = "idx_username", columnList = "username")},
    uniqueConstraints = {@UniqueConstraint(name = "uk_email", columnNames = "email")}
)
public class User {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @Column(nullable = false, unique = true)
    private String email;

    @Column(nullable = false)
    private String username;
}
```
  
## 📌 `@Table`을 활용한 다중 스키마 적용
  
### 3️⃣ 특정 스키마의 테이블을 매핑하는 예제
  
```java
@Entity
@Table(name = "employees", schema = "hr")
public class Employee {
    
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;
}
```
  
## 📌 장점과 단점
  
### ✅ 장점
- 테이블 이름을 명확하게 지정하여 **가독성을 높일 수 있음**  
- **스키마, 카탈로그 등 세부적인 설정 가능**  
- 인덱스 및 유니크 제약 조건을 설정하여 성능 향상 가능  
  
### ❌ 단점
- 잘못된 설정 시 매핑 오류가 발생할 수 있음  
- **테이블 구조 변경 시 코드도 함께 수정해야 함**  

---
  
# 연결문서
- [@Entity](../../jpa/jpa-@Entity)
- [@Column](../../jpa/jpa-@Column)
- [JPA](../../jpa/jpa-JPA)
