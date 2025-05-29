---
title : "Firewall"
excerpt : "Firewall"
toc : true
toc_sticky : true
toc_label : "Firewall"
categories:
- ServerCommon
tags:
- [ServerCommon]
last_modified_at: 2025-05-07T08:00:00-10:00:00
---
  
---
  
## 📌 Firewall(방화벽)이란?

> **info**
>
> Firewall은 **외부 네트워크와 내부 네트워크 간 트래픽을 제어하는 보안 시스템**이다.  
> 인가되지 않은 접근을 차단하고, 허용된 서비스만 통과시켜 **보안 경계를 형성**하는 역할을 한다. 
{: .notice--info}  

---
  
## ✅ 방화벽의 주요 기능

- **패킷 필터링**: IP, 포트, 프로토콜 기반으로 허용/차단
- **상태 기반 검사(Stateful Inspection)**: 연결 상태 기반 검사
- **애플리케이션 레벨 필터링**: 특정 앱 기반 제어 (L7 필터링)
- **로그 기록 및 모니터링**: 보안 이벤트 기록

---
  
## ✅ 방화벽의 유형

| 유형 | 설명 |
|------|------|
| 네트워크 방화벽 | 외부 ↔ 내부망 간 트래픽 제어 |
| 호스트 기반 방화벽 | 개별 서버나 PC에서 실행 |
| 차세대 방화벽 (NGFW) | DPI, IDS/IPS 통합 제공 |
| 웹 애플리케이션 방화벽 (WAF) | 웹 공격(SQLi, XSS 등) 차단 특화 |

---
  
## ✅ 방화벽 구성 예시

```
[인터넷] ⇄ [Firewall] ⇄ [DMZ: 웹서버] ⇄ [내부망: DB]
```

- 외부와 내부 사이에 방화벽을 배치하여 DMZ 및 내부망을 보호
- 특정 포트(예: 443)만 오픈하여 웹 서버에 접근 허용

---
  
## ✅ 주요 설정 요소

- 인바운드/아웃바운드 정책
- 허용/차단 포트 지정 (예: 22, 80, 443)
- 출발지/목적지 IP 범위
- 프로토콜(TCP/UDP/ICMP 등)

---
  
# 연결문서
- [IPS](../../servercommon/servercommon-IPS)
- [IDS](../../servercommon/servercommon-IDS)
