---
title : "JWT"
excerpt : "JWT"
toc : true
toc_sticky : true
toc_label : "JWT"
categories:
- ServerCommon
tags:
- [ServerCommon]
last_modified_at: 2025-05-07T08:00:00-10:00:00
---
  
---
  
## 📌 JWT(JSON Web Token)란?

> **info**
>
> JWT는 사용자 인증 정보를 JSON 형식으로 인코딩하여 만든 **디지털 토큰**이다.  
> 인증된 사용자의 신원을 증명하고, 서버 간의 **Stateless(무상태)** 통신을 가능하게 한다. 
{: .notice--info}  

---
  
## ✅ JWT의 구조

JWT는 `.`으로 구분된 **3개의 문자열로 구성**된다.

```
xxxxx.yyyyy.zzzzz
```

| 구성 요소 | 설명 |
|-----------|------|
| Header | 토큰 타입과 서명 알고리즘 (예: HS256) |
| Payload | 사용자 정보(Claims) 포함 (ex. userId, role 등) |
| Signature | 비밀키 기반의 서명값 (위조 방지) |

---
  
## ✅ JWT 예시
  
```json
Header: {
  "alg": "HS256",
  "typ": "JWT"
}

Payload: {
  "sub": "1234567890",
  "name": "John Doe",
  "role": "USER",
  "exp": 1682927358
}
```

---
  
## ✅ JWT의 특징

- **Stateless**: 서버에 세션 상태를 저장하지 않음
- **Self-contained**: 필요한 정보가 토큰 내부에 모두 포함
- **확장성**: 여러 서비스 간 인증 정보 공유 용이
- **보안 주의**: 민감 정보는 토큰에 직접 포함하지 말 것

---
  
## ✅ JWT 동작 흐름

1. 사용자가 로그인 → 서버에서 JWT 생성 후 응답
2. 클라이언트는 JWT를 로컬에 저장(LocalStorage, Cookie 등)
3. 이후 요청 시 `Authorization: Bearer <token>` 헤더로 전송
4. 서버는 토큰을 검증하여 사용자 인증 처리

---
  
## ✅ JWT vs 세션 기반 인증

| 항목 | JWT | 세션 |
|------|-----|------|
| 서버 상태 | Stateless | Stateful |
| 저장 위치 | 클라이언트 (브라우저) | 서버 (메모리/DB) |
| 확장성 | 뛰어남 (서버 간 공유 쉬움) | 낮음 |
| 보안 | 토큰 탈취 위험 존재 | 서버 보호 필요 |
| 로그아웃 처리 | 복잡 (블랙리스트 필요) | 세션 만료로 간단 |

---
  
## ✅ JWT 사용 시 주의 사항

- HTTPS 기반 통신 필수 (중간자 공격 방지)
- 짧은 만료 시간 설정 권장
- Refresh Token과 조합하여 사용
- 토큰 검증 시 서명 유효성 반드시 체크

---
  
# 연결문서
- [인증과 인가](../../servercommon/servercommon-인증과-인가)
- [SpringSecurity](../../spring/spring-SpringSecurity)
- [OAuth2](../../servercommon/servercommon-OAuth2)
