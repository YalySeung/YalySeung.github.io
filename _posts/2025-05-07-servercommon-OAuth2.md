---
title : "OAuth2"
excerpt : "OAuth2"
toc : true
toc_sticky : true
toc_label : "OAuth2"
categories:
- ServerCommon
tags:
- [ServerCommon]
last_modified_at: 2025-05-07T08:00:00-10:00:00
---
  
---
  
## 📌 OAuth 2.0이란?

> **info**
>
> OAuth 2.0은 **제3자 애플리케이션이 사용자의 비밀번호를 알지 않고도 자원에 접근할 수 있도록 권한을 위임하는 인증 프로토콜**이다.  
> 인증(Authentication)보다는 인가(Authorization)에 초점을 둔 방식이며, 대표적인 **토큰 기반 인가 프레임워크**이다. 
{: .notice--info}  

---
  
## ✅ 등장 배경

- SNS, 이메일, 클라우드 등 외부 서비스와 연동 필요 증가
- 사용자 비밀번호를 직접 공유하지 않고 인증 위임을 수행하기 위함

---
  
## ✅ 주요 개념

| 용어 | 설명 |
|------|------|
| Resource Owner | 자원 소유자 (ex. 사용자) |
| Client | 외부 애플리케이션 (ex. 앱, 웹) |
| Authorization Server | 인증을 수행하고 토큰 발급 |
| Resource Server | 보호된 자원(API 등)을 제공하는 서버 |
| Access Token | 자원 접근 권한을 가진 토큰 |
| Refresh Token | Access Token 갱신에 사용되는 토큰 |

---
  
## ✅ OAuth 2.0 동작 흐름

1. 사용자 → 클라이언트 로그인 요청
2. 클라이언트 → 인증서버에 권한 요청 (인가 코드 받음)
3. 클라이언트 → 인가 코드를 이용해 액세스 토큰 요청
4. 인증 서버 → 액세스 토큰 발급
5. 클라이언트 → 리소스 서버에 토큰 포함 요청
6. 리소스 서버 → 토큰 검증 후 데이터 응답

---
  
## ✅ 인가 방식 (Grant Types)

| 방식 | 설명 |
|------|------|
| Authorization Code | 가장 일반적, 서버-서버 환경에 적합 |
| Implicit | 클라이언트에서 토큰 직접 발급 (보안 취약) |
| Resource Owner Password | ID/PW 직접 입력 방식 (권장되지 않음) |
| Client Credentials | 클라이언트가 자체적으로 인증 (서버 간 통신) |

---
  
## ✅ OAuth2 vs JWT

| 항목 | OAuth2 | JWT |
|------|--------|-----|
| 개념 | 인증/인가 프로토콜 | 토큰 형식 |
| 목적 | 권한 위임 | 사용자 정보 전달 |
| 동작 방식 | 인증 서버 + 토큰 발급 | 토큰 자체에 정보 내포 |
| 사용 예시 | 구글 로그인, 카카오 로그인 | 사용자 상태 유지, API 인증 |

---
  
## ✅ OAuth2 적용 예시 (Spring Security)
  
```yaml
spring:
  security:
    oauth2:
      client:
        registration:
          google:
            client-id: xxxx
            client-secret: xxxx
            scope: profile, email
```

---
  
## ✅ OAuth2 사용 사례

- 소셜 로그인 (구글, 네이버, 카카오 등)
- 외부 애플리케이션과의 연동 API
- 사내 SSO 구현

---
  
# 연결문서
- [JWT](../../servercommon/servercommon-JWT)
- [인증과 인가](../../servercommon/servercommon-인증과-인가)
- [SpringSecurity](../../spring/spring-SpringSecurity)
