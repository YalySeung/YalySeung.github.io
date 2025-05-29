---
title : "영속성(Persistence)"
excerpt : "영속성(Persistence)"
toc : true
toc_sticky : true
toc_label : "영속성(Persistence)"
categories:
- ServerCommon
tags:
- [ServerCommon, Database]
last_modified_at: 2024-03-11T08:00:00-10:00:00
---
  
---
  
## 📌 영속성(Persistence)이란?

> **info**
>
> 영속성은 **프로그램이 종료된 이후에도 데이터가 유지되는 성질 또는 기능**을 말한다.  
> 주로 데이터베이스, 파일, 캐시 등 외부 저장소에 데이터를 저장해, 다음 실행 시에도 데이터를 유지할 수 있게 한다. 
{: .notice--info}  

---
  
## ✅ 영속성이 중요한 이유

- **데이터 보존**: 일시적인 메모리와 달리 재시작 후에도 데이터 유지
- **비즈니스 일관성 유지**: 장기적인 데이터 추적 및 복구
- **트랜잭션 관리**: 데이터 무결성과 정합성 유지

---
  
## ✅ 주요 영속성 저장 방식

| 저장 매체 | 설명 |
|-----------|------|
| 관계형 데이터베이스 | 가장 일반적인 형태 (MySQL, Oracle 등) |
| NoSQL | 유연한 스키마 구조 (MongoDB, Redis 등) |
| 파일 시스템 | 로그, 설정 등 텍스트 기반 저장 |
| 캐시 | 메모리 기반 고속 데이터 조회 (Redis, Memcached 등) |

---
  
## ✅ 대표적인 영속성 프레임워크

| 프레임워크 | 설명 |
|------------|------|
| JDBC | Java 기본 DB 연결 API, 저수준 |
| JPA | 자바 ORM 기반 추상화된 데이터 접근 방식 |
| Hibernate | JPA 구현체이자 확장 기능 제공 |
| MyBatis | SQL Mapper 기반의 반자동 ORM |

---
  
## ✅ 영속성과 ORM

- ORM(Object-Relational Mapping)은 **객체와 테이블 간의 매핑**을 자동화하여 영속성 처리 단계를 단순화함
- JPA, Hibernate 등은 ORM 기반의 대표적인 프레임워크

---
  
## ✅ 영속성 적용 예시 (JPA 기준)
  
```java
@Entity
public class User {
    @Id
    @GeneratedValue
    private Long id;

    private String name;
}
```
  
```java
userRepository.save(new User("홍길동")); // 데이터베이스에 저장
```

---
  
# 연결문서
- [JPA](../../jpa/jpa-JPA)
- [JDBC](../../servercommon/servercommon-JDBC)
- [Hibernate](../../jpa/jpa-Hibernate)
