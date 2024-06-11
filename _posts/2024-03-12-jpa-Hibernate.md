---
title : "Hibernate"
excerpt : "Hibernate"
toc : true
toc_sticky : true
toc_label : "Hibernate"
categories:
- JPA
tags:
- [Spring, Database, JPA]
last_modified_at: 2024-03-12T08:00:00-10:00:00
---
  
---
  
## 정의
> **Hibernate란?**  
>
> JPA의 구현체로 내부적으로 JDBC API를 사용하는 ORM Framework 
{: .notice--info}  
  
## 장점
- 패러다임 불일치(Java 와 DB의 구조적 불일치) 문제 해결
- 영속성 컨텍스트 제공
- 메서드 호출만으로 쿼리 수행
- 테이블 변경시 관련 DAO의 파라미터, 결과, SQL등을 대신 수행
- DB 변경 용이
  
## 단점
- 메서드 호출로 쿼리를 수행하는 것은 직접 SQL을 작성하는것보다 성능상 안좋음
- 메서드 호출만으로 DB 데이터 조작의 한계 => JPQL 사용 
{: .notice}  
- 진입장벽이 있음

---
  
# 연결문서
- [영속성(Persistence)](../../servercommon/servercommon-영속성(Persistence))
- [JPA](../../jpa/jpa-JPA)
- [JDBC](../../servercommon/servercommon-JDBC)
- [Querydsl](../../jpa/jpa-Querydsl)
- [HQL](../../jpa/jpa-HQL)