---
title : "ORM"
excerpt : "ORM"
toc : true
toc_sticky : true
toc_label : "ORM"
categories:
- ServerCommon
tags:
- [ServerCommon, Database]
last_modified_at: 2024-03-11T08:00:00-10:00:00
---
  
---
  
## 📌 ORM(Object-Relational Mapping) 정의

> **info**
>
> ORM은 데이터베이스의 테이블과 프로그래밍 언어의 객체 간의 **호환되지 않는 구조를 매핑**해주는 프로그래밍 기법이다.  
> 즉, SQL을 직접 작성하지 않고, 객체 지향 언어의 문법을 통해 DB 연산을 수행할 수 있도록 해준다. 
{: .notice--info}  

---
  
## ✅ ORM 동작 개념

- 클래스 ↔ 테이블
- 인스턴스 ↔ 레코드(Row)
- 필드 ↔ 컬럼
- 객체 간 연관관계 ↔ 외래키 기반 조인
  
![image](../../assets/images/ORMFunction.png)

---
  
## ✅ ORM의 장점
  
### 🔹 객체 지향적 구조

- SQL 대신 메서드 기반 접근 → 가독성 향상
- 선언/할당/종료 등 부수적인 코드 감소
- 객체와 DB 매핑 정보가 명확하게 유지됨
  
### 🔹 리팩토링 용이

- 클래스와 객체 기반이므로 유지보수가 쉬움
- DB 스키마 변경에 유연하게 대응 가능
- ERD 의존성 감소
  
### 🔹 DBMS 종속성 감소

- 다양한 RDBMS에 이식 가능
- SQL 자동 생성 → RDBMS 교체 시 코드 변경 최소화

---
  
## ✅ ORM의 단점
  
### 🔹 설계의 어려움

- 프로젝트 복잡도에 따라 설계 난이도 증가
- 설계 미흡 시 성능 저하 가능 (N+1, 지연 로딩 등)
- 복잡한 쿼리는 Native SQL 또는 튜닝 필요
  
### 🔹 진입 장벽 존재

- DB 설계에 대한 이해 필요
- 영속성 컨텍스트, 플러시, 트랜잭션 전파 등 학습 필요

---
  
## ✅ 대표 ORM 프레임워크

| 언어 | 프레임워크 |
|------|-------------|
| Java | JPA, Hibernate |
| Python | Django ORM |
| JavaScript | Sequelize, TypeORM |
| PHP | Doctrine |

---
  
## ✅ ORM vs SQL 직접 작성

| 항목 | ORM | SQL |
|------|-----|-----|
| 코드 유지보수 | 유리함 | 불리함 |
| 성능 제어 | 튜닝 필요 | 세밀한 제어 가능 |
| 학습 난이도 | 높음 | 비교적 쉬움 |
| 생산성 | 높음 | 낮음 |

---
  
# 연결문서
- [JPA](../../jpa/jpa-JPA)
- [Hibernate](../../jpa/jpa-Hibernate)
- [영속성(Persistence)](../../servercommon/servercommon-영속성(Persistence))
