---
title : "@Column"
excerpt : "@Column"
toc : true
toc_sticky : true
toc_label : "@Column"
categories:
- JPA
tags:
- [Spring, Annotation, JPA]
last_modified_at: 2024-04-27T08:00:00-10:00:00
---
  
---
  
 이 글에서는 [@Entity](../../jpa/jpa-@Entity)를 구성하는데 필수적인 @Column Annotation에 대해서 알아보겠다. 

 @Column Annotation은 [JPA](../../jpa/jpa-JPA) 에서 Entity 클래스의 **필드와 데이터베이스 테이블의 컬럼 간의 매핑을 정의**할때 사용한다. 주요한 기능은 **필드의 다양한 속성을 지정**하는 것이다.
  
## ✅ 결론부터
> 🔹 **DDL 생성(`ddl-auto=create|update`) 시 Hibernate가 일부는 알아서 생성해주지만** 
> 🔹 정확한 제약 조건(`nullable`, `length` 등)을 반영하려면  
> 👉 `@Column` 속성들을 **명시적으로 설정하는 것이 가장 안전**하다 
{: .notice}  

 @Column Annotation의 주요 속성을 살펴보자.

| 속성               | 기능                           |
| ---------------- | ---------------------------- |
| name             | 컬럼명 설정                       |
| length           | 데이터 Max 길이 설정                |
| nullable         | null값 가능 여부 설정               |
| precision        | 숫자 타입에서 전체 자리수를 지정           |
| scale            | 숫자 타입 필드에서 소수부 자리수를 지정       |
| columnDefinition | 컬럼 타입 지정                     |
| unique           | 해당 컬럼의 값이 유일해야 하는지 여부를 지정    |
| insertable       | 이 필드가 INSERT 쿼리에 포함될지 여부를 지정 |
| updatable        | 이 필드가 UPDATE 쿼리에 포함될지 여부를 지정 |

 아래 소스코드는 Entity의 필드를 선언하는 몇가지 예시이다.
  
```java
// Float 타입의 최대 길이와 소수부 자리수를 지정
@Column(name = "AVG_CPU_USE_RATE", precision = 5, scale = 2)  
private Float averageCpuUseRate;

// max 길이만 설정
@Column(name = "TASK_ORD_DT", length = 6, nullable = false)  
private DateTime orderDateTime;

//Lob 타입 지정
@Lob  
@Column(name = "QUE_DATA", columnDefinition = "CLOB")  
private String queueData;
```

---
  
# 연결문서
- [@Entity](../../jpa/jpa-@Entity)
- [JPA](../../jpa/jpa-JPA)