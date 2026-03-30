---
title : "Google Cloud Platform"
excerpt : "Google Cloud Platform"
toc : true
toc_sticky : true
toc_label : "Google Cloud Platform"
categories:
- ServerCommon
tags:
- [ServerCommon, Backend, Cloud]
last_modified_at: 2026-03-30T08:00:00-10:00:00
---
  
---
  
> **info**
>
> Google Cloud Platform(GCP)의 개념과 주요 서비스, 그리고 실무에서의 활용 포인트를 정리한다.  
> **핵심은 “인프라를 코드로 관리하고, 확장성과 운영 효율을 극대화하는 것”이다.** 
{: .notice--info}  

---
  
## 📌 GCP란?

 Google Cloud Platform(GCP)은 Google이 제공하는 클라우드 컴퓨팅 서비스로,  
 서버, 스토리지, 네트워크, 데이터베이스, AI 등 다양한 인프라를 서비스 형태로 제공한다.
  
### ✅ 특징

- 글로벌 인프라 (Google 데이터센터 기반)
- 사용량 기반 과금 (Pay-as-you-go)
- 자동 확장 (Auto Scaling)
- DevOps 친화적 구조

---
  
## 📌 클라우드 vs 온프레미스

| 구분 | 온프레미스 | 클라우드(GCP) |
|------|-----------|----------------|
| 서버 구축 | 직접 구매 | 즉시 생성 |
| 확장성 | 제한적 | 무제한 확장 |
| 비용 | 초기 비용 큼 | 사용량 기반 |
| 운영 | 직접 관리 | 관리 최소화 |

> **tip**
>
> **클라우드는 CAPEX → OPEX 전환이라고 보면 이해가 빠르다** 
{: .notice--info}  

---
  
## 📌 핵심 서비스 구성
  
### 1️⃣ Compute (서버)

- Compute Engine (VM)
- Kubernetes Engine (GKE)
- App Engine
- Cloud Run
  
```text
사용 시나리오
- API 서버 → Compute Engine / GKE
- MSA → Kubernetes (GKE)
- 간단 서비스 → Cloud Run
```

---
  
### 2️⃣ Storage (저장소)

- Cloud Storage (Object Storage)
- Persistent Disk (VM 디스크)
- Filestore (파일 시스템)

---
  
### 3️⃣ Database

- Cloud SQL (MySQL, PostgreSQL)
- Firestore (NoSQL)
- BigQuery (데이터 분석)

---
  
### 4️⃣ Networking

- VPC
- Load Balancer
- Cloud CDN

---
  
### 5️⃣ DevOps & 운영

- Cloud Build (CI/CD)
- Artifact Registry
- Cloud Monitoring
- Cloud Logging

---
  
## 📌 GCP 아키텍처 예시
  
```text
[Client]
   ↓
[Load Balancer]
   ↓
[GKE / Compute Engine]
   ↓
[Cloud SQL / Firestore]
   ↓
[Cloud Storage]
```

---
  
## 📌 실무 활용 패턴
  
### ✅ 1. Spring Boot API 서버

- Compute Engine 또는 GKE에 배포
- Cloud SQL 연동
  
```text
Spring Boot → GKE → Cloud SQL
```

---
  
### ✅ 2. 이미지/파일 처리 시스템

- 업로드: Cloud Storage
- 처리: Cloud Run / GKE
- 결과 저장: DB + Storage

---
  
### ✅ 3. 로그 및 모니터링

- Cloud Logging → 로그 수집
- Cloud Monitoring → 메트릭 분석
- Alerting → 장애 대응

---
  
## 📌 GCP 사용 시 고려사항
  
### 🚨 비용 관리

- VM 계속 켜두면 비용 증가
- Auto Scaling 활용 필수

---
  
### 🚨 네트워크 설계

- VPC, Subnet 설계 중요
- 방화벽 정책 명확히 설정

---
  
### 🚨 보안

- IAM 최소 권한 원칙 적용
- Service Account 사용

---
  
## 📌 장점과 단점
  
### ✅ 장점

- 빠른 인프라 구축
- 높은 확장성
- 운영 자동화
  
### ❌ 단점

- 비용 예측 어려움
- 클라우드 종속성 (Vendor Lock-in)

---
  
## 📌 온프레미스 vs GCP 선택 기준

| 상황 | 추천 |
|------|------|
| 금융/폐쇄망 | 온프레미스 |
| 스타트업 | GCP |
| 트래픽 변동 큼 | GCP |
| 레거시 시스템 | 온프레미스 |

---
  
## 📌 정리

> [!summary]  
> GCP는 단순 인프라 제공이 아니라 **서비스 운영 플랫폼**이다. 
{: .notice}  

- 서버를 직접 관리하지 않고
- 자동 확장과 운영 자동화를 활용하며
- DevOps 중심으로 설계하는 것이 핵심이다.

---
  
# 연결문서
