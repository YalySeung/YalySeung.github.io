---
title : "인증과 인가"
excerpt : "인증과 인가"
toc : true
toc_sticky : true
toc_label : "인증과 인가"
categories:
- ServerCommon
tags:
- [ServerCommon]
last_modified_at: 2024-01-09T08:00:00-10:00:00
---
  
---
  
## 📌 인증(Authentication)이란?

> **info**
>
> 인증은 사용자가 **자신이 누구인지를 증명하는 과정**이다.  
> 주로 ID/비밀번호, OTP, 생체 정보, 인증서 등을 통해 본인 확인을 수행한다. 
{: .notice--info}  

---
  
## 📌 인가(Authorization)란?

> **info**
>
> 인가는 **인증된 사용자가 특정 자원이나 기능에 접근 가능한지를 결정하는 과정**이다.  
> 역할(Role), 권한(Permission), 정책 기반으로 접근 제어가 이뤄진다. 
{: .notice--info}  

---

![](98.Resources/Images/AuthenticationAndAuthoriztion.png)

---
  
## ✅ 인증 vs 인가 비교

| 항목 | 인증(Authentication) | 인가(Authorization) |
|------|------------------------|----------------------|
| 목적 | 사용자의 신원 확인 | 권한 검증 및 접근 제어 |
| 시점 | 보통 먼저 수행됨 | 인증 이후에 수행됨 |
| 데이터 기반 | 사용자 정보(ID, PW 등) | 사용자 권한(Role, Access Level) |
| 기술 예시 | 로그인, SSO, OAuth 인증 | RBAC, ACL, URL 접근 제어 등 |
| 결과 | 사용자 세션 생성 또는 토큰 발급 | 요청 자원 허용 여부 판단 |

---
  
## ✅ 인증 방식 예시

- **Basic Authentication**: ID/PW를 Base64로 인코딩해 전송 (보안 취약)
- **Form 기반 인증**: 사용자 입력 폼을 통해 인증
- **OAuth 2.0 / OIDC**: 외부 인증 제공자(Google, Kakao 등) 사용
- **JWT (JSON Web Token)**: 토큰 기반 인증, Stateless 방식

---
  
## ✅ 인가 방식 예시

- **Role 기반 인가 (RBAC)**: 사용자에게 역할을 부여하고 역할에 따라 접근 제어
- **URL 패턴 인가**: `/admin/**`는 관리자만 허용 등
- **Method/Annotation 기반 인가**: `@PreAuthorize("hasRole('ADMIN')")` 등

---
  
## ✅ Spring Security 연동 흐름 예시

1. 사용자가 로그인 시도 → Authentication 객체 생성
2. `AuthenticationManager`가 `UserDetailsService`와 함께 인증 처리
3. 인증 성공 → `SecurityContextHolder`에 보안 정보 저장
4. 요청 시 `AccessDecisionManager`가 인가 판단

---
  
# 연결문서
- [SpringSecurity](../../spring/spring-SpringSecurity)
- [JWT](../../servercommon/servercommon-JWT)
- [OAuth2](../../servercommon/servercommon-OAuth2)
- [RBAC](../../itbusiness/itbusiness-RBAC)
