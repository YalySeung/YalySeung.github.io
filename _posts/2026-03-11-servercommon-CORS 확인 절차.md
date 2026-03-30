---
title : "CORS 확인 절차"
excerpt : "CORS 확인 절차"
toc : true
toc_sticky : true
toc_label : "CORS 확인 절차"
categories:
- ServerCommon
tags:
- [SpringBoot, Backend, Web, ServerCommon]
last_modified_at: 2026-03-11T08:00:00-10:00:00
---
  
---
  
## 개요

 backend_boot 개발 프로젝트에서 Web ↔ Backend 통신 시 **CORS 문제를 감지하고 원인을 분석하는 절차**를 정리한다.  
 브라우저 환경에서는 서버가 정상 응답을 반환하더라도 **CORS 정책에 의해 응답이 차단**될 수 있다.

 따라서 다음 절차를 통해 문제를 단계적으로 확인한다.

---
  
## 1️⃣ 브라우저 Console 확인

 브라우저에서 개발자 도구를 열고 Console 로그를 확인한다.

단축키

```
F12
```

대표적인 CORS 에러

```
Access to fetch at 'API_URL' from origin 'WEB_URL' has been blocked by CORS policy
```

 의미

- 브라우저가 보안 정책에 의해 응답을 차단
- 서버 응답 여부와 별개로 발생 가능

---
  
## 2️⃣ Network 탭 요청 분석

 개발자 도구 → **Network 탭**에서 요청을 확인한다.

 확인해야 할 항목

- Request URL
- Request Method
- Status Code
- Response Header

특히 다음 Header 존재 여부 확인

```
Access-Control-Allow-Origin
Access-Control-Allow-Methods
Access-Control-Allow-Headers
Access-Control-Allow-Credentials
```

 이 값이 없거나 중복으로 존재하면, 브라우저는 응답을 차단한다.

---
  
## 3️⃣ Preflight (OPTIONS) 요청 확인

 다음 조건일 때 브라우저는 **Preflight 요청(OPTIONS)**을 먼저 보낸다.

조건

- Authorization Header 사용
- Content-Type: application/json
- PUT / DELETE / PATCH 요청

확인 방법

Network 탭에서

```
OPTIONS /api/...
```

요청 존재 여부 확인

문제 유형

| 상황 | 원인 |
|-----|-----|
| OPTIONS 401 / 403 | Spring Security 차단 |
| OPTIONS 404 | Controller 매핑 문제 |
| OPTIONS 200 but Request Fail | CORS Header 누락 |

---
  
## 4️⃣ curl로 서버 직접 확인

 브라우저 문제인지 서버 문제인지 확인하기 위해 curl 테스트를 수행한다.

Origin Header 포함 요청

```
curl -i https://api.example.com \
-H "Origin: https://web.example.com"
```

Preflight 테스트

```
curl -i -X OPTIONS https://api.example.com \
-H "Origin: https://web.example.com" \
-H "Access-Control-Request-Method: POST"
```

 확인 포인트

- Access-Control-Allow-Origin 존재 여부
- Access-Control-Allow-Methods 존재 여부

---
  
## 5️⃣ Spring Boot 설정 확인

 backend_boot 프로젝트에서는 다음 위치에서 CORS 설정을 확인한다.

확인 대상

- SecurityConfig
- WebMvcConfigurer
- CorsFilter

예시
  
```java
@Override
public void addCorsMappings(CorsRegistry registry) {
    registry.addMapping("/**")
        .allowedOrigins("*")
        .allowedMethods("GET","POST","PUT","DELETE","OPTIONS")
        .allowedHeaders("*");
}
```

---
  
## 결론

 Web에서 CORS 문제 발생 시 다음 순서로 확인한다.

1. **Console 로그 확인**
2. **Network 요청 분석**
3. **OPTIONS Preflight 확인**
4. **curl 테스트 수행**
5. **Spring Boot CORS 설정 확인**

 이 절차를 따르면 대부분의 CORS 문제를 빠르게 진단할 수 있다.

---
  
# 연결문서
- [CORS](../../servercommon/servercommon-CORS)
- [SpringSecurity](../../spring/spring-SpringSecurity)
- [HTTP](../../servercommon/servercommon-HTTP)
