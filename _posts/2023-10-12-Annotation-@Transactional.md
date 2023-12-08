---
title : "@Transactional"
excerpt : "@Transactional"
toc : true
toc_sticky : true
toc_label : "@Transactional"
categories:
- Annotation
tags:
- [Spring, Annotation]
last_modified_at: 2023-10-12T08:00:00-10:00:00
---

# 날짜 : 2023-10-12 14:58

# 태그 : #Spring #Annotation
---

# 내용

## Artifact 
- **spring-tx**

## 역할
- 트랜잭션을 관리하고 제어
- 메서드 레벨에서 트랜잭션을 시작, 커밋 또는 롤백하는 데 사용. 데이터베이스 작업을 원자적으로 처리 할 수 있음
- 트랜잭션 내에서 예외가 발생하면 롤백 처리
- 이외에 다양한 트랜잭션 속성 설정 가능
	- 격리 수준, 읽기전용 여부, 타임아웃 등

## 트랜잭션 격리 수준
- 여러 트랜잭션이 동시에 실행될 때, 데이터베이스의 일관성을 어떻게 관리할 것인지 정의
- **DEFAULT:** 기본 격리 수준은 데이터베이스 또는 트랜잭션 매니저에 따라 다를 수 있으며 가장 보편적인 격리 수준을 사용합니다.
- **READ_UNCOMMITTED:** 다른 트랜잭션에서 커밋하지 않은 변경 사항도 읽을 수 있으며, 가장 낮은 격리 수준입니다. 일관성이 낮고 더 많은 동시성을 제공합니다.
- **READ_COMMITTED:** 다른 트랜잭션에서 커밋한 변경 사항만 읽을 수 있으며, 기본 격리 수준입니다. 일관성이 중간 수준이며 일반적으로 사용됩니다. 
- **REPEATABLE_READ:** 한 트랜잭션 내에서 반복 읽기는 항상 동일한 결과를 반환하며, 다른 트랜잭션의 변경 사항은 읽을 수 없습니다.
- **SERIALIZABLE:** 동시성이 가장 낮으며 가장 엄격한 격리 수준입니다. 모든 변경 사항을 다른 트랜잭션과 공유하지 않습니다.

---

# 연결문서
- [SpringMVC](../../Spring/Spring-SpringMVC)
- [SpringMVC 구현](../../Spring/Spring-SpringMVC-구현)