---
title : "IDS"
excerpt : "IDS"
toc : true
toc_sticky : true
toc_label : "IDS"
categories:
- ServerCommon
tags:
- [하드웨어, ServerCommon]
last_modified_at: 2025-05-07T08:00:00-10:00:00
---
  
---
  
## 📌 IDS (Intrusion Detection System)란?

> **info**
>
> IDS는 Intrusion Detection System의 약자로, **네트워크나 시스템에서 비정상적인 활동을 탐지하고 경고하는 보안 장비**이다.  
> 탐지만 수행하며, 차단은 하지 않는 **수동적 보안 시스템**이다. 
{: .notice--info}  

---
  
## ✅ IDS의 주요 기능

- **서명 기반 탐지(Signature-based)**: 알려진 공격 패턴 탐지
- **이상 탐지 기반(Anomaly-based)**: 비정상 행동 탐지
- **로그 분석**: 네트워크 및 시스템 로그 분석
- **알림/경고**: 관리자에게 침입 시도 알림 전송

---
  
## ✅ IDS 유형

| 유형 | 설명 |
|------|------|
| NIDS (Network IDS) | 네트워크 상의 패킷을 감시 |
| HIDS (Host IDS) | 서버 또는 시스템 내 활동 모니터링 |
| 하이브리드 IDS | NIDS + HIDS 통합 방식 |

---
  
## ✅ IDS vs IPS 비교

| 항목 | IDS | IPS |
|------|-----|-----|
| 역할 | 탐지 및 경고 | 실시간 차단 |
| 반응 | 수동 | 능동 |
| 위치 | 미러 포트 등 감시용 | Inline 실시간 중간 |
| 사용 목적 | 로그 기록, 분석 | 실시간 방어 |

---
  
## ✅ 한계점

- **실시간 차단 불가**
- **오탐/과탐 가능성**
- **전문가의 상시 분석 필요**

> **tip**
>
> IDS는 단독보다는 IPS, WAF, SIEM 등과 연동되어 보완적으로 사용됨 
{: .notice--info}  

---
  
# 연결문서
- [IPS](../../servercommon/servercommon-IPS)
- [Firewall](../../servercommon/servercommon-Firewall)