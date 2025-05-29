---
title : "서버 이중화"
excerpt : "서버 이중화"
toc : true
toc_sticky : true
toc_label : "서버 이중화"
categories:
- ServerCommon
tags:
- [ServerCommon]
last_modified_at: 2023-12-08T08:00:00-10:00:00
---
  
---
  
## 📌 서버 이중화(Server Redundancy)란?

> **info**
>
> 서버 이중화는 **시스템 가용성과 안정성을 확보**하기 위해 동일한 기능을 수행하는 **두 대 이상의 서버를 구성**하는 기술이다.  
> 장애 발생 시 **서비스 중단을 최소화**하고, **데이터 보호**와 **업타임 향상**을 목표로 한다. 
{: .notice--info}  

---
  
## ✅ 서버 이중화의 주요 목적

- **고가용성(High Availability)**: 장애 발생 시 다른 서버가 자동으로 서비스 인계
- **로드 밸런싱(Load Balancing)**: 여러 서버 간 트래픽 분산 처리
- **재해 복구(Disaster Recovery)**: 자연재해나 예기치 못한 사고 시 복구 가능

---
  
## ✅ 서버 이중화 구성 방식
  
### 🔹 Active-Standby 방식

![](Active_Standby.png)

- 하나의 서버는 **활성 상태(Active)**, 다른 하나는 **대기 상태(Standby)**
- 주기적으로 **Heartbeat 신호**를 주고받아 장애 감지
- 실시간으로 **데이터 동기화**하여 일관성 유지
- 장애 발생 시 Standby 서버가 자동 승격되어 서비스 지속

---
  
### 🔹 Active-Active 방식

![](Active_Active.png)

- 두 서버 모두 **동시에 활성 상태로 서비스 제공**
- **로드 밸런서(L4/L7)**를 통해 요청 분산
- 성능 향상과 부하 분산에 유리
- 한쪽 서버에 장애가 발생해도 다른 서버가 요청을 처리함

---
  
## ✅ 이중화 기술 적용 예

| 구성 요소 | 이중화 방식 | 예시 |
|-----------|--------------|------|
| 웹 서버 | Active-Active | Apache, Nginx + L4 |
| DB 서버 | Active-Standby | MySQL Replication, PostgreSQL Streaming |
| 애플리케이션 | Hybrid | WAS 이중화 |
| 데이터 저장소 | RAID + 이중화 NAS | Synology, QNAP |

---
  
## ✅ 고려 사항

- **데이터 동기화 방식** (실시간/지연)
- **장애 전환 시간(Failover Time)**
- **네트워크 부하/지연**
- **이중화 구성에 따른 비용 증가**
- **정기 테스트 및 모니터링**

---
  
# 연결문서
- [LoadBalancer](../../servercommon/servercommon-LoadBalancer)
- [RAID](../../하드웨어/하드웨어-RAID)
- [재해복구시스템(DR)](../../servercommon/servercommon-재해복구시스템(DR))
