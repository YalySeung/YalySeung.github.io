---
title : "@Entity"
excerpt : "@Entity"
toc : true
toc_sticky : true
toc_label : "@Entity"
categories:
- JPA
tags:
- [Spring, Annotation, JPA, Querydsl]
last_modified_at: 2024-04-03T08:00:00-10:00:00
---
  
---
  
 이 글에서는 JPA를 적용하는데 핵심적인 @Entity Annotation에 대해서 알아보자.

 @Entity Annotation은 DB 테이블에 대응하는 하나의 Class를 정의 할 때 사용한다. @Entity 가 적용되면 JPA의 관리대상이 되며, DB와 Mapping 된다.
  
```java
@Entity
@Data
@NoArgsConstructor @AllArgsConstructor
@Table(name = "user")  
public class User {  
	...
}
```

> **caution**
>
> 대상 Class는 public 혹은 protected인 기본 생성자가 필요함.  final class, enum, interface, inner class에 사용하지 않도록 한다. 
{: .notice--danger}  

---
  
# 연결문서
- [JPA](../../jpa/jpa-JPA)
- [Spring Data Jpa](../../jpa/jpa-Spring-Data-Jpa)
- [@Table](../../annotation/annotation-@Table)
- [@Data](../../annotation/annotation-@Data)
- [@GeneratedValue](../../jpa/jpa-@GeneratedValue)