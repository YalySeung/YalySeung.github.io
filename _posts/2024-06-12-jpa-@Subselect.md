---
title : "@Subselect"
excerpt : "@Subselect"
toc : true
toc_sticky : true
toc_label : "@Subselect"
categories:
- JPA
tags:
- [Spring, JPA, Annotation]
last_modified_at: 2024-06-12T08:00:00-10:00:00
---
  
---
  
> **`@Subselect`란?**  
>
>  Hibernate에서 **Inline View를 엔티티처럼 사용할 수 있도록 지원하는 어노테이션**이다. 
{: .notice--info}  

  `@Subselect`를 활용하면 **데이터베이스 테이블을 변경하지 않고도 복잡한 쿼리를 엔티티로 매핑할 수 있다.**  
  특히 Querydsl 및 Hibernate 환경에서 `FROM` 절의 Inline View가 필요한 경우 사용된다.
  
## 사용법
  
### 1️⃣ `@Subselect` 적용 예제
  
```java
import org.hibernate.annotations.Immutable;
import org.hibernate.annotations.Subselect;

import javax.persistence.Entity;
import javax.persistence.Id;

@Entity
@Immutable // 엔티티는 읽기 전용
@Subselect(
    "SELECT e.id AS id, e.name AS name, COUNT(o.id) AS order_count " +
    "FROM employee e " +
    "LEFT JOIN orders o ON e.id = o.employee_id " +
    "GROUP BY e.id, e.name"
)
public class EmployeeOrderSummary {

    @Id
    private Long id;
    private String name;
    private Long orderCount;
}
```
  
## 장점과 단점
  
### ✅ 장점
- **데이터베이스 테이블을 변경하지 않고도 엔티티 매핑 가능**  
- **복잡한 쿼리를 엔티티처럼 활용하여 코드 가독성 향상**  
- **Querydsl 및 Hibernate 환경에서 활용 가능**  
  
### ❌ 단점
- **읽기 전용 엔티티이므로 데이터 변경 불가능**  
- **JPA 표준이 아니므로 Hibernate에 종속됨**  

---
  
# 연결문서
- [Querydsl](../../jpa/jpa-Querydsl)
- [Hibernate](../../jpa/jpa-Hibernate)
