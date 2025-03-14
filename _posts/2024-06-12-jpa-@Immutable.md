---
title : "@Immutable"
excerpt : "@Immutable"
toc : true
toc_sticky : true
toc_label : "@Immutable"
categories:
- JPA
tags:
- [JPA, Spring]
last_modified_at: 2024-06-12T08:00:00-10:00:00
---
  
---
  
> **`@Immutable` 이란?**  
>
> JPA에서 엔티티를 변경 불가능(Immutable)하게 설정하는 Hibernate 어노테이션이다. 
{: .notice--info}  

  `@Immutable`은 Hibernate에서 제공하는 어노테이션으로, **조회 전용 엔티티**를 만들 때 사용된다.  
  해당 엔티티는 데이터베이스에서 값을 조회할 수 있지만, 변경이 불가능하다.
  
## @Immutable 사용 방법
  JPA 엔티티에서 `@Immutable`을 적용하면 Hibernate가 변경 감지를 수행하지 않는다.
  
```java
import org.hibernate.annotations.Immutable;

@Entity
@Immutable
public class ReadOnlyEntity {
    
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    
    private String name;
}
```
  
## @Immutable의 특징
- **JPA의 변경 감지 기능이 비활성화됨**  
- **`save()`, `update()` 등의 변경 작업이 불가능**  
- **트랜잭션이 끝나도 데이터 변경이 반영되지 않음**  
- **주로 View 테이블, 로그 테이블과 같은 읽기 전용 데이터에 사용**  
  
## @Immutable vs @ReadOnly
  
| 어노테이션 | 제공 라이브러리 | 주요 기능 |
|------------|--------------|-----------|
| `@Immutable` | Hibernate | 변경 감지 비활성화, 저장 불가 |
| `@ReadOnly` | Spring Data JPA | 단순 읽기 전용, 업데이트 가능 |
  
## @Immutable의 장점과 단점
  
### ✅ 장점
- Hibernate가 변경 감지를 수행하지 않으므로 **성능 최적화 가능**  
- 읽기 전용 데이터를 안전하게 유지 가능  
  
### ❌ 단점
- 데이터 변경이 필요한 경우 새로운 엔티티를 생성해야 함  
- JPA 표준 어노테이션이 아니라 Hibernate에 종속됨  

---
  
# 연결문서
- [JPA](../../jpa/jpa-JPA)
- [Hibernate](../../jpa/jpa-Hibernate)
