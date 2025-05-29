---
title : "재해복구시스템(DR)"
excerpt : "재해복구시스템(DR)"
toc : true
toc_sticky : true
toc_label : "재해복구시스템(DR)"
categories:
- ServerCommon
tags:
- [DevelopCommon]
last_modified_at: 2024-10-04T08:00:00-10:00:00
---
  
---
  
## 📌 재해복구시스템(DR, Disaster Recovery)란?

> **info**
>
> 재해복구시스템(DR)은 기업이나 조직에서 예기치 못한 **재난(자연재해, 사이버 공격, 장애 등)**이 발생했을 때,  
> IT 인프라, 데이터, 애플리케이션 등의 **서비스 연속성을 보장**하기 위한 전략 및 기술 체계이다. 
{: .notice--info}  

---
  
## ✅ DR 시스템의 주요 요소

1. **RTO (Recovery Time Objective)**  
   - 시스템이나 서비스가 중단된 후 복구되기까지의 **최대 허용 시간**
2. **RPO (Recovery Point Objective)**  
   - 복구 시 허용 가능한 **데이터 손실 시점**
3. **복제 및 이중화 인프라**  
   - On-Premise 또는 클라우드 기반의 **이중화된 데이터 센터** 보유
4. **복구 기술 및 계획**  
   - 데이터 백업, 복제, 가상화, DR 시나리오 문서화 및 주기적 테스트

---
  
## ✅ DR 아키텍처 유형

| 유형              | 설명 |
|-------------------|------|
| On-Site DR        | 동일 장소 내에서 운영, 빠른 복구 가능하나 재해 영향 가능 |
| Off-Site DR       | 다른 지역의 물리적 복구센터, 재해 안전성 높음, 복구 속도는 느릴 수 있음 |
| 클라우드 기반 DR  | 퍼블릭/프라이빗 클라우드 활용, 유연성과 확장성 우수, 비용 효율적 |

---
  
## ✅ 관련 핵심 기술

- **실시간 데이터 복제**: 비동기 또는 동기 방식으로 DR 대상지와 데이터 일치 유지
- **자동화 도구 (Orchestration)**: 복구 시 수동 개입 없이 자동 절차 실행 (예: AWS CloudFormation, Azure Site Recovery)
- **멀티리전 구성**: 지리적으로 분산된 데이터 센터 운영
- **DR 시나리오 테스트**: 주기적 복구 연습 및 계획 점검

---
  
## ✅ 클라우드 DR 서비스 예시

| 클라우드 | DR 서비스 |
|----------|-----------|
| AWS      | AWS Backup, AWS Disaster Recovery |
| Azure    | Azure Site Recovery |
| GCP      | Backup and DR Service |

---
  
# 연결문서
- [서버 이중화](../../servercommon/servercommon-서버-이중화)
