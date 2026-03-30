---
title : "web_cors 감지절차"
excerpt : "web_cors 감지절차"
toc : true
toc_sticky : true
toc_label : "web_cors 감지절차"
categories:
- DevelopCommon
tags:
- [CORS, SpringBoot, Backend, Web, DevTools, Troubleshooting]
last_modified_at: 2026-03-02T08:00:00-10:00:00
---
  
---
  
## 개요
 Web에서 CORS(Cross-Origin Resource Sharing) 이슈를 **감지/재현/원인분리** 하는 절차를 `backend_boot` 개발 프로젝트 경험을 기준으로 정리한다.  
 (계정/도메인/내부 IP/토큰/DB 접속정보 등 민감정보는 모두 일반화된 형태로 기술한다.)

---
  
## CORS 감지의 핵심 포인트
 CORS는 “서버가 막았다”라기보다, **브라우저가 보안 정책으로 응답을 차단**하는 케이스가 대부분이다.  
 따라서 “요청이 서버에 도달했는지”와 “브라우저가 차단했는지”를 분리해서 보는 게 중요하다.

---
  
## 1️⃣ 브라우저 콘솔에서 1차 감지

 1) 브라우저에서 문제가 발생한 화면을 열고 `F12` → **Console** 탭 확인  
 2) 아래 형태 메시지가 보이면 CORS 가능성이 높다.
  
```text
Access to fetch at 'https://api.example.com/...' from origin 'https://web.example.com'
has been blocked by CORS policy:
No 'Access-Control-Allow-Origin' header is present on the requested resource.
```
  
```text
Response to preflight request doesn't pass access control check:
It does not have HTTP ok status.
```

> **note**
>
> - **No 'Access-Control-Allow-Origin'**: 서버가 CORS 헤더를 안 주거나, 조건 불일치
> - **preflight request**: OPTIONS 사전요청이 실패했을 가능성 
{: .notice--info}  

---
  
## 2️⃣ Network 탭에서 요청 흐름 추적

 Network 탭에서 실제로 어떤 요청이 나갔는지 확인하면 원인 분리가 빠르다.
  
### 2-1. 필터링 방법
 - `Fetch/XHR` 필터 선택
 - 문제 API 경로 일부로 검색 (예: `/api`, `/auth`, `/v1`)
  
### 2-2. 확인 체크리스트
 - Request URL: 프론트 Origin과 다른지 확인 (Origin mismatch 여부)
 - Request Method: `GET/POST/PUT/DELETE` 등
 - Status Code: `200/401/403/404/500` 등
 - **OPTIONS** 요청 존재 여부 (Preflight)
 - Response Headers에 CORS 헤더 존재 여부
  
### 2-3. CORS 관련 헤더 확인 포인트
**Request Headers**
- `Origin: https://web.example.com`
- `Access-Control-Request-Method: POST` (preflight에서만)
- `Access-Control-Request-Headers: authorization, content-type` (preflight에서만)

**Response Headers**
- `Access-Control-Allow-Origin: https://web.example.com` (또는 `*`)
- `Access-Control-Allow-Methods: GET,POST,...`
- `Access-Control-Allow-Headers: Authorization, Content-Type,...`
- `Access-Control-Allow-Credentials: true` (쿠키/세션 포함 시)

> **warning**
>
> `credentials: include`(쿠키/세션) 사용 중이면 `Access-Control-Allow-Origin: *` 는 사용할 수 없다.  
> 이 경우는 반드시 **정확한 Origin**을 내려줘야 한다. 
{: .notice--info}  

---
  
## 3️⃣ Preflight(OPTIONS) 실패 케이스 분류

 Preflight가 생기는 조건은 대체로 아래 중 하나다.
 - `Authorization` 헤더 사용
 - `Content-Type: application/json` 등 “simple request”가 아닌 타입
 - `PUT/DELETE/PATCH` 같은 메서드 사용
  
### 3-1. 실패 유형 A: OPTIONS가 401/403
 서버 보안(Spring Security/필터/게이트웨이)에서 OPTIONS를 막는 경우다.

**증상**
- Network에 OPTIONS가 찍히고 Status가 401/403
- Console에는 “preflight doesn't pass...” 류 문구

**대응 방향**
- OPTIONS 요청은 인증 없이 통과시키는 정책 필요
- 또는 Security chain 앞단에서 OPTIONS를 허용
  
### 3-2. 실패 유형 B: OPTIONS는 200인데 실제 요청이 CORS 차단
 헤더 설정이 누락/불일치한 경우가 많다.

**증상**
- OPTIONS 200
- 실제 API 응답에 `Access-Control-Allow-Origin`이 없거나 Origin이 다름

**대응 방향**
- CORS 설정을 **필터/프레임워크 레벨에서 일관**되게 적용
- (Spring Boot) WebMvcConfigurer / CorsFilter / Spring Security CORS 연동 중 하나로 통일
  
### 3-3. 실패 유형 C: 리다이렉트(301/302) 때문에 실패
 프록시/로드밸런서/리버스프록시에서 http→https redirect가 걸리면 preflight가 실패할 수 있다.

**증상**
- OPTIONS가 301/302
- Location 헤더로 다른 URL로 이동

**대응 방향**
- CORS 처리는 **최종 응답을 만드는 지점**에서 수행
- 프록시 단계에서 redirect 정책 재점검

---
  
## 4️⃣ curl로 브라우저 없이 “서버 응답 헤더” 검증

 브라우저가 차단하는 케이스라도, 서버가 무엇을 내려주는지 curl로 확인하면 빠르다.
  
### 4-1. 일반 요청에서 CORS 헤더 확인
  
```bash
curl -i "https://api.example.com/v1/health"   -H "Origin: https://web.example.com"
```
  
### 4-2. Preflight(OPTIONS) 시뮬레이션
  
```bash
curl -i -X OPTIONS "https://api.example.com/v1/resource"   -H "Origin: https://web.example.com"   -H "Access-Control-Request-Method: POST"   -H "Access-Control-Request-Headers: authorization,content-type"
```

> **tip**
>
> curl 결과에서 `Access-Control-Allow-*` 헤더가 **없는지/값이 맞는지**만 봐도 80%는 결론이 난다. 
{: .notice--info}  

---
  
## 5️⃣ 운영 관점 체크리스트 (backend_boot 기준)

 CORS 이슈는 “코드 설정”만으로 끝나지 않고, 운영 구성(프록시/도메인/보안정책)과 결합될 때 터진다.

- 프론트 배포 도메인과 API 도메인이 다른지 (서브도메인 포함)
- 프록시(Nginx/ALB/Gateway)에서 CORS 헤더를 덮어쓰는지
- Spring Security 필터 체인에서 OPTIONS를 차단하는지
- Authorization 헤더/JSON content-type 때문에 preflight가 발생하는지
- 쿠키 기반 세션이면 `Allow-Credentials`와 Origin이 올바른지
- 에러 응답(401/403/500)에도 CORS 헤더가 포함되는지  
  → 에러 응답에서 헤더가 빠지면 “정상인데도 브라우저가 막는 것처럼” 보일 수 있다.

---
  
## 6️⃣ 결론: 감지 절차 요약

- Console로 1차 CORS 의심
- Network 탭으로 **OPTIONS 존재/상태코드/헤더** 확인
- 실패 유형(401/403, 헤더누락, redirect)으로 분류
- curl로 서버 응답 헤더를 재현 검증
- 운영 구성(프록시/보안/쿠키)까지 포함해 원인 확정

---
  
# 연결문서
- [SpringSecurity](../../spring/spring-SpringSecurity)
- [Swagger](../../servercommon/servercommon-Swagger)
- [Nginx](../../servercommon/servercommon-Nginx)
- [HTTP](../../servercommon/servercommon-HTTP)
- [CORS](../../servercommon/servercommon-CORS)
