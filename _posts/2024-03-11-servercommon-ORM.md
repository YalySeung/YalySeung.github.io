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

# 날짜 : 2024-03-11 19:48

# 태그 : #ServerCommon #Database
---

# 내용

## 정의
> **ORM이란?**
>
> Object Relational Mapping
> 데이터베이스와 객체 지향 프로그래밍 언어 간의 호환되지 않는 데이터를 변환하는 프로그래밍 기법
{: .notice--info}

![image](../../assets/images/ORMFunction.png)

## 장점

### 객체 지향적 구조
- SQL이 아닌 클래스 메서드를 통해 데이터베이스를 조작 가능
- SQL의 선언, 할당, 종료 같은 부수적인 코드를 줄일 수 있음
- 객체에 대한 코드를 별도로 작성하여 코드의 가독성 향상

### 리팩토링 용이
- 객체지향적이기때문에 리팩토링이 용이하다
- 매핑하는 정보가 명확하기 때문에 ERD 의존도가 낮음

### DBMS 종속성 감소
- 객체간 관계를 바탕으로 SQL문을 자동 생성하고, 객체의 자료형 타입까지 사용할 수 있어 RDBMS의 데이터 구조와 객체지향 모델의 간격을 줄일 수 있음
- DBMS 교체 용이

## 단점

### 설계의 어려움
- 프로젝트의 복잡성과 비례하여 난이도 증가
- 설계가 부족할 경우 속도 및 일관성 저하
- 일부 자주 사용되는 복잡한 SQL문은 속도를 위한 별도 튜닝이 필요

### 진입 장벽
- ORM을 제대로 활용하려면 DBMS에 대한 정확한 이해와 ORM의 작동원리, 순서에 대한 깊은 이해가 바탕이 되어야 함
- 많은 학습 시간 필요

## ORM Frameworks
- [JPA](../../servercommon/servercommon-JPA), [Hibernate](../../servercommon/servercommon-Hibernate)
- Sequelize
- Django ORM

---

# 연결문서
- [JPA](../../servercommon/servercommon-JPA)
- [Hibernate](../../servercommon/servercommon-Hibernate)
- [영속성(Persistence)](../../servercommon/servercommon-영속성(Persistence))