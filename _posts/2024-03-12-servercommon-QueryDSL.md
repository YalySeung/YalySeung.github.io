---
title : "QueryDSL"
excerpt : "QueryDSL"
toc : true
toc_sticky : true
toc_label : "QueryDSL"
categories:
- ServerCommon
tags:
- [ServerCommon, Database]
last_modified_at: 2024-03-12T08:00:00-10:00:00
---

# 날짜 : 2024-03-12 16:48

# 태그 : #ServerCommon #Database
---

# 내용

## 정의
> **QueryDSL이란?**
>
> Query Domain Specific Language
> Hibernate Query Language를 타입에 맞게 안전하게 생성 및 관리해주는 Builder Opensource Framework
{: .notice--info}

## 장점
- java 소스로 쿼리를 작성할 수 있어, 컴파일 시점에 Syntax Error 확인 가능
- IDE의 자동완성 기능 사용 가능
- 복잡한 Query와 동적 Query 작성이 용이함
- Query 작성 시, 제약조건등을 메서드로 추출하여 재사용 가능

## Example

```java
String productName = "myProduct";

List<Product> result = queryFactory
        .select(product)
        .from(product)
        .where(usernameEq(productName))
        .fetch();
```

---

# 연결문서
- [JPA](../../servercommon/servercommon-JPA)
- [Hibernate](../../servercommon/servercommon-Hibernate)
- [ORM](../../servercommon/servercommon-ORM)
- [JPQL](../../servercommon/servercommon-JPQL)