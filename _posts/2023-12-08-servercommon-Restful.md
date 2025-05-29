---
title : "Restful"
excerpt : "Restful"
toc : true
toc_sticky : true
toc_label : "Restful"
categories:
- ServerCommon
tags:
- [ServerCommon, BackEnd, RESTAPI]
last_modified_at: 2023-12-08T08:00:00-10:00:00
---
  
---
  
## 📌 RESTful 이란?

> **info**
>
> RESTful은 Respresentational State Transfer의 개념을 **웹 기반 분산 시스템 아키텍처**에 적용한 것이다.  
> 클라이언트-서버 구조의 HTTP 기반 시스템에서 **리소스를 URI로 표현하고, 상태 전이를 HTTP Method로 표현**하는 방식이다. 
{: .notice--info}  

---
  
## ✅ RESTful 아키텍처 구성요소

| 요소 | 설명 |
|------|------|
| Resource | URI로 명명되는 자원 (예: `/users/1`) |
| Method | HTTP Method (GET, POST, PUT, DELETE 등) |
| Representation | 요청/응답 본문에 포함된 데이터 표현 (JSON, XML 등) |

---
  
## ✅ REST의 핵심 원칙
  
### 🔹 Uniform Interface
- 리소스에 대한 인터페이스는 통일되어 있어야 함 (GET/POST/PUT/DELETE 등)
  
### 🔹 Stateless
- 요청 간 클라이언트 상태를 서버가 유지하지 않음 → 확장성과 단순성 증가
  
### 🔹 Cacheable
- HTTP의 캐싱 기능 사용 가능 → 트래픽 감소 및 응답 속도 향상
  
### 🔹 Self-descriptive Messages
- 메시지 자체에 요청 정보를 충분히 담고 있어야 함
  
### 🔹 Client-Server 구조
- 클라이언트는 UI 및 요청 처리, 서버는 비즈니스 로직 및 데이터 처리 담당
  
### 🔹 계층화 구조
- 프록시, 로드 밸런서, 보안 계층 등을 중간에 추가 가능

---
  
## ✅ RESTful URI 설계 원칙

| 원칙 | 설명 |
|------|------|
| 명사형 URI | 리소스 중심 표현 (`/users`, `/orders/1`) |
| 계층 표현 | `/users/1/orders` → 사용자 1의 주문 |
| 소문자 사용 | 대소문자 혼용 지양 |
| 하이픈(-) 사용 | 단어 구분은 하이픈 사용 |
| 확장자 미포함 | `Accept` 헤더로 표현 형식 지정 |
| 동사는 HTTP Method로 표현 | `/users/delete/1` ❌ → `DELETE /users/1` ✅

---
  
## ✅ HTTP Method와 리소스 매핑

| Method | 용도 |
|--------|------|
| GET | 리소스 조회 |
| POST | 리소스 생성 |
| PUT | 리소스 전체 수정 |
| PATCH | 리소스 일부 수정 |
| DELETE | 리소스 삭제 |

---
  
## ✅ 예시: 직원 리소스 관리 API
  
```http
GET /worker/얄리
POST /worker
{
  "name": "얄리",
  "team": "연구1팀"
}

PUT /worker/얄리
{
  "team": "Q서비스팀"
}

DELETE /worker/얄리
```

---
  
## ✅ RESTful에서의 Resource 개념

- **Collection**: 리소스들의 묶음 (예: `/users`)
- **Document**: 단일 리소스 (예: `/users/1`)
- **Store**: 파일 또는 바이너리 리소스를 저장하는 경우
- **Controller**: 자원 자체가 아닌 동작을 제어하는 URI (예: `/auth/login`)

---
  
## ✅ 설계 팁

- `PathVariable`은 고유 식별자 전달 시 사용
- `RequestParam`은 필터링, 검색 등 조건 전달 시 사용
- 민감 정보 포함된 조회는 POST 사용 고려
- 삽입용 POST와 조회용 POST는 URI로 구분

---
  
# 연결문서
- [HTTP Method](../../servercommon/servercommon-HTTP-Method)
- [REST API 설계](../../servercommon/servercommon-REST-API-설계)
