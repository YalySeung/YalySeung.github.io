---
title : "HTTP Method"
excerpt : "HTTP Method"
toc : true
toc_sticky : true
toc_label : "HTTP Method"
categories:
- ServerCommon
tags:
- [ServerCommon, HTTP]
last_modified_at: 2023-11-29T08:00:00-10:00:00
---
  
---
  
> **HTTP Method란?**  
>
>  HTTP 요청을 보낼 때 사용되는 다양한 메서드로, 클라이언트와 서버 간의 데이터 전송 방식을 정의한다. 
{: .notice--info}  

  HTTP 메서드는 **RESTful API에서 자원을 조작하는 기본적인 방법**이며, 각 메서드는 특정한 목적을 가지고 있다.
  
## 📌 HTTP Method 종류 및 특징
  
### 1️⃣ GET (조회)
- 특정 **리소스를 받고 싶을 때 사용**하는 메서드  
- 요청시 필요한 정보는 **query parameter**로 전달  
- **리소스 생성, 수정, 삭제에는 사용하지 않음**  
- 응답 데이터가 캐싱될 가능성이 있음
  
```http
GET /users?id=123 HTTP/1.1
Host: example.com
```
  
### 2️⃣ POST (생성 및 실행 요청)
- **리소스 생성, 컨트롤러 실행을 위한 요청** 시 사용  
- 요청시 필요한 정보는 **request body**에 포함  
- 서버에 데이터를 전송하는 대표적인 방식
  
```http
POST /users HTTP/1.1
Host: example.com
Content-Type: application/json

{
    "name": "홍길동",
    "email": "hong@example.com"
}
```
  
### 3️⃣ PUT (전체 업데이트)
- 변경 가능한 **리소스 전체를 업데이트**할 때 사용  
- 요청시 필요한 정보는 **request body**에 전달  
- 업데이트할 리소스의 **식별 정보**가 포함되어야 함
  
```http
PUT /users/123 HTTP/1.1
Host: example.com
Content-Type: application/json

{
    "name": "홍길동",
    "email": "hong_updated@example.com"
}
```
  
### 4️⃣ PATCH (부분 업데이트)
- 변경 가능한 **리소스의 일부 속성만 업데이트**할 때 사용  
- PUT과 마찬가지로 **리소스 식별 정보 포함 필요**  
- PUT을 사용해 전체 객체를 업데이트하는 것이 관례여서 **거의 사용되지 않음**
  
```http
PATCH /users/123 HTTP/1.1
Host: example.com
Content-Type: application/json

{
    "email": "hong_patch@example.com"
}
```
  
### 5️⃣ DELETE (삭제)
- 특정 **리소스를 제거**하기 위한 메서드  
- 일반적으로 **Request Body 없이 URI 경로에 리소스 ID를 포함**
  
```http
DELETE /users/123 HTTP/1.1
Host: example.com
```
  
### 6️⃣ HEAD (헤더 조회)
- 클라이언트가 **본문 없이 리소스의 헤더 정보만 조회**하는 메서드  
- 리소스의 존재 여부 확인 및 메타데이터 검사 용도로 사용
  
```http
HEAD /users/123 HTTP/1.1
Host: example.com
```
  
### 7️⃣ OPTIONS (지원 메서드 조회)
- 클라이언트가 **서버의 특정 리소스에 대해 수행 가능한 동작을 조회**할 때 사용  
- 서버는 **Allow 헤더에 사용 가능한 HTTP 메서드를 반환**
  
```http
OPTIONS /users HTTP/1.1
Host: example.com
```

**서버 응답 예시**:
  
```http
HTTP/1.1 200 OK
Allow: GET, POST, PUT, DELETE, OPTIONS
```

---
  
## 📌 RESTful API에서 HTTP 메서드 활용
  
| HTTP Method | 사용 목적 | 멱등성 |
|-------------|----------|--------|
| GET | 리소스 조회 | ✅ |
| POST | 리소스 생성 또는 실행 | ❌ |
| PUT | 리소스 전체 업데이트 | ✅ |
| PATCH | 리소스 부분 업데이트 | ❌ |
| DELETE | 리소스 삭제 | ✅ |
| HEAD | 리소스 존재 여부 확인 | ✅ |
| OPTIONS | 사용 가능한 HTTP 메서드 조회 | ✅ |

> **멱등성(Idempotency)**  
>
> **한 요청을 여러 번 수행해도 결과가 동일하게 유지되는 성질**을 의미함.  
> 예를 들어, `GET`, `PUT`, `DELETE`는 멱등하지만, `POST`와 `PATCH`는 요청을 반복할 경우 상태가 달라질 수 있음. 
{: .notice--info}  

---
  
# 연결문서
- [HTTP](../../servercommon/servercommon-HTTP)
- [Restful](../../servercommon/servercommon-Restful)
