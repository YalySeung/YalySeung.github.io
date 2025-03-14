---
title : "OAuth"
excerpt : "OAuth"
toc : true
toc_sticky : true
toc_label : "OAuth"
categories:
- DevelopCommon
tags:
- [DevelopCommon]
last_modified_at: 2024-04-14T08:00:00-10:00:00
---
  
---
  
> **OAuth란?**  
>
> Open Authorization의 약어로, 애플리케이션 권한 인증에 구글, 카카오 등 제3의 서비스에 저장된 계정 정보를 활용하는 인증 방법이다. 
{: .notice--info}  
  
## OAuth의 주요 개념
- OAuth는 사용자의 비밀번호를 직접 입력하지 않고도 타사 애플리케이션이 사용자 정보를 안전하게 접근할 수 있도록 설계된 **인증 프레임워크**
- **인증(Authentication)과 인가(Authorization)의 개념을 분리**하여 보안 강화  
- **토큰 기반 인증 방식 사용 (Access Token, Refresh Token)**  
  
## OAuth의 동작 방식

1️⃣ **사용자가 애플리케이션에서 OAuth 로그인을 선택**  
2️⃣ **OAuth 제공자(Google, Facebook 등)로 리디렉트됨**  
3️⃣ **사용자가 로그인 후 애플리케이션에 대한 접근 권한을 부여**  
4️⃣ **OAuth 제공자가 Access Token을 발급**  
5️⃣ **애플리케이션이 API 요청 시 Access Token을 포함하여 사용자 데이터 요청**  
  
## OAuth 2.0 인증 방식

| 인증 방식              | 설명                            | 사용 예               |
| ------------------ | ----------------------------- | ------------------ |
| Authorization Code | 가장 안전한 방식으로, 코드 교환 후 토큰 발급    | 웹 애플리케이션           |
| Implicit           | 브라우저에서 직접 토큰을 발급받는 방식 (보안 취약) | SPA (현재 사용 권장 안 함) |
| Password Grant     | 사용자 아이디/비밀번호로 직접 인증 (보안 취약)   | 내부 서비스용            |
| Client Credentials | 서버 간 통신에서 사용되는 인증 방식          | API 서비스            |
  
## OAuth의 장점과 단점
  
### ✅ 장점
- 사용자의 **비밀번호를 노출하지 않고도 인증 가능**  
- **소셜 로그인을 통한 빠른 접근 가능**  
- API를 통한 **서비스 확장 용이**  
  
### ❌ 단점
- **Access Token 유출 시 보안 위험**  
- **OAuth 제공자의 정책에 따라 서비스 제한 가능**  
- 구현 방식이 복잡할 수 있음

---
  
# 연결문서
- [인증과 인가](../../servercommon/servercommon-인증과-인가)
