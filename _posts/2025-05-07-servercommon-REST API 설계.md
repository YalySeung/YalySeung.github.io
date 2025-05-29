---
title : "REST API 설계"
excerpt : "REST API 설계"
toc : true
toc_sticky : true
toc_label : "REST API 설계"
categories:
- ServerCommon
tags:
- [ServerCommon]
last_modified_at: 2025-05-07T08:00:00-10:00:00
---
  
---
  
## 📌 REST API 설계 가이드

> **info**
>
> REST API는 리소스를 명확히 표현하고, HTTP Method를 적절히 사용하는 것이 핵심이다.  
> 이 문서는 일관된 API 설계를 위한 명명 규칙, URI 구성, 응답 구조 등을 가이드한다. 
{: .notice--info}  

---
  
## ✅ URI 설계 원칙
  
### 🔹 리소스 중심

- 명사는 복수형으로 작성 (`/users`, `/orders`)
- 하위 리소스는 경로로 표현 (`/users/{userId}/orders`)
- 동사는 HTTP Method로 표현 (예: `POST /users`)
  
### 🔹 일관된 스타일

| 항목 | 예시 |
|------|------|
| 전체 조회 | `GET /items` |
| 단일 조회 | `GET /items/{id}` |
| 생성 | `POST /items` |
| 수정 (전체) | `PUT /items/{id}` |
| 수정 (일부) | `PATCH /items/{id}` |
| 삭제 | `DELETE /items/{id}` |

---
  
## ✅ URI 작성 규칙

| 규칙 | 예시 |
|------|------|
| 소문자 사용 | `/users`, `/accounts` |
| 하이픈(-)으로 단어 구분 | `/user-profile` |
| 확장자 사용 금지 | `/users.json` ❌ |
| 쿼리스트링은 필터용 | `/users?age=30` |

---
  
## ✅ 응답 포맷 가이드
  
```json
{
  "status": 200,
  "message": "성공",
  "data": {
    "userId": 1,
    "username": "얄리"
  }
}
```

| 필드 | 설명 |
|------|------|
| `status` | HTTP 상태코드와 동일 |
| `message` | 간단한 결과 메시지 |
| `data` | 응답 데이터 본문 |

---
  
## ✅ 상태 코드 표준

| 상태코드 | 의미 |
|----------|------|
| 200 OK | 성공 |
| 201 Created | 생성 성공 |
| 204 No Content | 삭제 성공, 본문 없음 |
| 400 Bad Request | 잘못된 요청 |
| 401 Unauthorized | 인증 실패 |
| 403 Forbidden | 권한 없음 |
| 404 Not Found | 리소스 없음 |
| 409 Conflict | 중복 리소스 등 충돌 |
| 500 Internal Server Error | 서버 에러 |

---
  
## ✅ 에러 응답 구조 예시
  
```json
{
  "status": 400,
  "message": "잘못된 요청입니다",
  "error": {
    "field": "email",
    "reason": "이메일 형식이 잘못되었습니다"
  }
}
```

---
  
## ✅ 버전 관리

- URL 버전 권장: `/api/v1/users`
- Header 버전 대안: `Accept: application/vnd.myapp.v1+json`

---
  
## ✅ 인증 및 권한 처리

| 방식 | 설명 |
|------|------|
| JWT | 토큰 기반 인증 방식, 클라이언트 저장 |
| OAuth2 | 외부 인증 시스템과 연계 |
| Session | 서버 저장 방식 (Spring Security 등 활용)

---
  
# 연결문서
- [Restful](../../servercommon/servercommon-Restful)
- [HTTP Method](../../servercommon/servercommon-HTTP-Method)
- [JWT](../../servercommon/servercommon-JWT)
- [OAuth2](../../servercommon/servercommon-OAuth2)
