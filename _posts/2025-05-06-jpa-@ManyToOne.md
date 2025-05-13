---
title : "@ManyToOne"
excerpt : "@ManyToOne"
toc : true
toc_sticky : true
toc_label : "@ManyToOne"
categories:
- JPA
tags:
- [JPA]
last_modified_at: 2025-05-06T08:00:00-10:00:00
---
  
---
  
## 📌 `@ManyToOne(fetch = FetchType.LAZY)` 설명

> **info**
>
> `@ManyToOne`은 JPA에서 엔티티 간 N:1 관계를 매핑할 때 사용하는 어노테이션이다. 
{: .notice--info}  
  
### ✅ 기본 구조
  
```java
@ManyToOne(fetch = FetchType.LAZY)
@JoinColumn(name = "user_id", nullable = false)
private User user;
```

---
  
## ✅ 구성 요소
  
### 🔹 `@ManyToOne`
- 현재 엔티티가 여러 개이고, 상대 엔티티는 하나일 때 사용 (예: 여러 게시글 → 하나의 사용자)
- 관계의 주인이다 (foreign key를 관리)
  
### 🔹 `fetch = FetchType.LAZY`
- 연관된 엔티티를 실제 사용할 때까지 로딩하지 않음 (지연 로딩)
- 성능 최적화를 위해 기본적으로 사용 권장

| FetchType | 설명 |
|-----------|------|
| `EAGER`   | 연관된 엔티티를 즉시 함께 로딩 |
| `LAZY`    | 실제 사용할 때 로딩 (프록시로 대체) |

---
  
## ✅ 장점과 주의사항
  
### ✅ 장점
- 불필요한 쿼리 실행 방지 → 성능 향상
- 필요한 순간까지 DB 접근을 늦춰 리소스 절약
  
### ⚠️ 주의
- LAZY 로딩된 엔티티를 JSON으로 직렬화할 경우 `hibernateLazyInitializer` 오류 발생 가능
- 이를 해결하려면 DTO 변환 또는 Jackson 설정 필요

---
  
## ✅ 예시: 게시글과 사용자
  
```java
@Entity
public class Post {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String content;

    @ManyToOne(fetch = FetchType.LAZY)
    @JoinColumn(name = "user_id")
    private User user;
}
```

- `Post` 엔티티 여러 개가 하나의 `User`에 매핑된다.
- `user_id` 컬럼은 외래 키 역할

---
  
# 연결 문서
- [@Entity](../../jpa/jpa-@Entity)