---
title : "JPOQL"
excerpt : "JPOQL"
toc : true
toc_sticky : true
toc_label : "JPOQL"
categories:
- ServerCommon
tags:
- [ServerCommon]
last_modified_at: 2024-04-24T08:00:00-10:00:00
---
  
---
  
## 📌 JPOQL이란?

> **info**
>
> JPOQL(Java Persistent Object Query Language)은 JDO(Java Data Objects)에서 사용되는 **객체 지향 쿼리 언어**이다.  
> SQL과 유사하지만, 객체와 필드 중심으로 동작하며 **관계, 상속, 다형성**을 지원한다. 
{: .notice--info}  

---
  
## ✅ JPOQL의 특징

- **SQL과 유사한 문법**이지만, 객체 필드와 관계 위주로 설계됨
- **객체 지향 프로그래밍에 최적화**된 쿼리 처리 방식
- **상속과 다형성 지원**: 슈퍼타입 또는 서브타입 필터링 가능
- **JDOQL과 유사하게 동작하며**, 도메인 클래스 중심으로 쿼리 작성

---
  
## ✅ 기본 문법
  
```sql
SELECT FROM com.example.User
WHERE this.age > 20 && this.active ** true
```

- `this`: 현재 쿼리 대상 객체를 가리킴
- 필드 접근은 `this.fieldName` 방식 사용

---
  
## ✅ 메서드 지원 예시

| 구문 | 설명 |
|------|------|
| `startsWith("abc")` | 문자열 시작 여부 |
| `endsWith("xyz")`   | 문자열 끝 여부 |
| `matches("정규표현식")` | 정규식 매칭 |
| `contains("값")` | 포함 여부 검사 |

---
  
## ✅ 예시: 필터링 + 정렬
  
```sql
SELECT FROM com.domain.Order
WHERE totalAmount > 5000
ORDER BY orderDate DESC
```

---
  
## ✅ 예시: 관계 탐색
  
```sql
SELECT FROM com.domain.Employee
WHERE department.name ** "HR"
```

- 객체 간 관계를 통해 연관된 필드 접근 가능

---
  
## ✅ 주의사항

- SQL 함수 일부는 미지원
- 복잡한 조인보다 객체 모델링을 우선 고려
- 데이터베이스 독립적 추상화이므로 DB 특화 기능은 한계가 있음

---
  
# 연결문서
- [JDO](../../servercommon/servercommon-JDO)
- [JPA](../../jpa/jpa-JPA)
- [JPQL](../../jpa/jpa-JPQL)
