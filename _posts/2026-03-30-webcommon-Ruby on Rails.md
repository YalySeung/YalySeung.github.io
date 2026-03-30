---
title : "Ruby on Rails"
excerpt : "Ruby on Rails"
toc : true
toc_sticky : true
toc_label : "Ruby on Rails"
categories:
- WebCommon
tags:
- [Backend]
last_modified_at: 2026-03-30T08:00:00-10:00:00
---
  
---
  
> **info**
>
> Ruby on Rails(RoR)의 개념과 구조, 그리고 실무에서의 활용 방식을 정리한다.  
> **핵심은 “Convention over Configuration 기반의 빠른 개발 생산성”이다.** 
{: .notice--info}  

---
  
## 📌 Ruby on Rails란?

 Ruby on Rails는 Ruby 언어 기반의 웹 애플리케이션 프레임워크로,  
 빠른 개발을 위해 다양한 규칙과 자동화를 제공한다.
  
### ✅ 특징

- Convention over Configuration (설정보다 규칙)
- DRY (Don't Repeat Yourself)
- 풀스택 프레임워크
- 빠른 프로토타이핑

---
  
## 📌 핵심 개념
  
### 1️⃣ MVC 패턴
  
```text
Model   → 데이터 및 비즈니스 로직
View    → 사용자 인터페이스
Controller → 요청 처리 및 흐름 제어
```

> **tip**
>
> **Rails는 MVC를 강제하는 구조로 코드 일관성이 높다** 
{: .notice--info}  

---
  
### 2️⃣ Convention over Configuration

- 파일 위치, 네이밍 규칙이 정해져 있음
- 설정 최소화
- 개발 속도 극대화

예:
  
```text
User 모델 → users 테이블 자동 매핑
```

---
  
### 3️⃣ Active Record

- ORM(Object Relational Mapping)
- DB 테이블 ↔ 객체 자동 매핑
  
```ruby
class User < ApplicationRecord
end
```

---
  
## 📌 프로젝트 구조
  
```text
app/
  ├─ models/
  ├─ controllers/
  ├─ views/
config/
db/
public/
```

---
  
## 📌 주요 기능
  
### ✅ 1. Routing
  
```ruby
Rails.application.routes.draw do
  resources :users
end
```

---
  
### ✅ 2. Migration
  
```ruby
class CreateUsers < ActiveRecord::Migration[6.0]
  def change
    create_table :users do |t|  

      t.string :name
    end
  end
end
```

---
  
### ✅ 3. Scaffold
  
```bash
rails generate scaffold User name:string
```

> **tip**
>
> **Scaffold를 통해 CRUD를 빠르게 생성 가능** 
{: .notice--info}  

---
  
## 📌 Rails vs Spring Boot

| 항목 | Rails | Spring Boot |
|------|------|-------------|
| 언어 | Ruby | Java |
| 구조 | Convention 중심 | Configuration 중심 |
| 생산성 | 매우 빠름 | 상대적으로 느림 |
| 확장성 | 중간 | 매우 높음 |
| 생태계 | 스타트업 중심 | 엔터프라이즈 중심 |

---
  
## 📌 실무 활용 패턴
  
### ✅ 스타트업 MVP

- 빠른 개발 필요
- 초기 서비스 구축

---
  
### ✅ Admin 시스템

- CRUD 중심 서비스
- 내부 관리 시스템

---
  
### ✅ API 서버

- Rails API 모드 활용
  
```bash
rails new myapp --api
```

---
  
## 📌 장점과 단점
  
### ✅ 장점

- 빠른 개발 속도
- 높은 생산성
- 코드 일관성
  
### ❌ 단점

- 성능 튜닝 어려움
- 대규모 시스템에서 한계
- Ruby 생태계 축소

---
  
## 📌 사용 시 고려사항
  
### 🚨 성능

- N+1 문제 주의
- 캐싱 전략 필요

---
  
### 🚨 구조 확장

- MSA 전환 시 어려움
- 서비스 분리 필요

---
  
### 🚨 인력 수급

- Ruby 개발자 부족

---
  
## 📌 정리

> [!summary]  
> Ruby on Rails는 **빠른 개발을 위한 생산성 중심 프레임워크**이다. 
{: .notice}  

- 스타트업 MVP에 최적화
- CRUD 기반 서비스에 강점
- 대규모 시스템에서는 구조적 한계 존재

---
  
# 연결문서
- [SpringBoot-Project](../../springboot/springboot-SpringBoot-Project)
- [SpringMVC](../../spring/spring-SpringMVC)