---
title : "JDO"
excerpt : "JDO"
toc : true
toc_sticky : true
toc_label : "JDO"
categories:
- ServerCommon
tags:
- [ServerCommon, Database]
last_modified_at: 2024-04-24T08:00:00-10:00:00
---
  
---
  
## 📌 JDO(Java Data Objects)란?

> **info**
>
> JDO는 Java 객체를 데이터베이스에 영속화(Persistence)하기 위한 **Java 표준 API**이다.  
> 관계형 DB 뿐만 아니라 객체형 DB에서도 활용 가능한 **범용 객체 영속화 프레임워크**로, ORM과 유사하지만 더 다양한 저장소에 대한 추상화를 제공한다. 
{: .notice--info}  

---
  
## ✅ JDO의 주요 특징

- Java 객체 ↔ DB 간 매핑 지원 (Persistence by reachability)
- 표준 쿼리 언어인 **JDOQL** 제공 (JPQL 유사)
- **트랜잭션 관리**, **캐싱**, **지연 로딩(Lazy Loading)**, **관계 매핑** 등 지원
- JDBC와 ORM의 장점 모두 보유

---
  
## ✅ JDO 구성 요소

| 구성요소 | 설명 |
|----------|------|
| `PersistenceManagerFactory` | 설정 기반 영속성 매니저 생성 |
| `PersistenceManager` | DB 연동 및 객체 조작 주체 |
| `Transaction` | 트랜잭션 시작/커밋/롤백 관리 |
| `Extent` | 특정 클래스 전체 인스턴스 접근 |

---
  
## ✅ JDO 주요 용도

- Java 객체 모델을 기반으로 **RDB, OODB, NoSQL** 등 다양한 저장소 연동
- 도메인 주도 설계(DDD) 환경에서 **모델 중심의 영속성 처리**
- 데이터 접근 코드를 단순화하여 **생산성과 유지보수성 향상**

---
  
## ✅ JDO vs JPA 비교

| 항목 | JDO | JPA |
|------|-----|-----|
| 표준 쿼리 | JDOQL | JPQL |
| 연동 DB | RDB + OODB + 기타 저장소 | 주로 RDB |
| 구현체 | DataNucleus, Versant 등 | Hibernate, EclipseLink 등 |
| 표준화 시점 | JSR 12, 243 | JSR 220 |

---
  
## ✅ 예시 코드 (DataNucleus 기반)
  
```java
PersistenceManagerFactory pmf = JDOHelper.getPersistenceManagerFactory("Tutorial");
PersistenceManager pm = pmf.getPersistenceManager();
Transaction tx = pm.currentTransaction();

try {
    tx.begin();
    Person p = new Person("홍길동", 35);
    pm.makePersistent(p);
    tx.commit();
} finally {
    if (tx.isActive()) tx.rollback();
    pm.close();
}
```

---
  
# 연결문서
- [영속성(Persistence)](../../servercommon/servercommon-영속성(Persistence))
- [JPOQL](../../servercommon/servercommon-JPOQL)
- [JPA](../../jpa/jpa-JPA)
