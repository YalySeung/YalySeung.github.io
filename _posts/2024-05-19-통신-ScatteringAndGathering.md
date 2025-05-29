---
title : "ScatteringAndGathering"
excerpt : "ScatteringAndGathering"
toc : true
toc_sticky : true
toc_label : "ScatteringAndGathering"
categories:
- 통신
tags:
- [통신]
last_modified_at: 2024-05-19T08:00:00-10:00:00
---
  
---
  
## 📌 Scattering이란?

> **info**
>
> **Scattering**은 하나의 데이터 소스에서 여러 목적지로 데이터를 **분산 전송**하는 과정을 말한다.  
> 분산 처리를 위해 데이터를 여러 노드에 나누어 보내는 방식으로, 네트워크 통신이나 병렬 처리에서 자주 사용된다. 
{: .notice--info}  

![](98.Resources/Images/ScatteringWorkFlow.png)

---
  
## 📌 Gathering이란?

> **info**
>
> **Gathering**은 여러 소스에서 데이터를 수집하여 하나의 목적지로 **집약**하는 과정이다.  
> 분산된 데이터를 하나로 합치는 작업으로, 데이터 병합이나 통계 수집에 활용된다. 
{: .notice--info}  

![](98.Resources/Images/GatheringWorkFlow.png)

---
  
## ✅ 병렬 컴퓨팅에서의 활용 (MPI 기반)

MPI (Message Passing Interface)는 병렬 컴퓨팅 환경에서 데이터를 송수신하기 위한 표준 라이브러리로, 다음과 같은 함수들을 제공한다:

- `MPI_Scatter`: 데이터를 여러 프로세스에 분배
- `MPI_Gather`: 여러 프로세스에서 데이터를 수집
  
### ✳️ 예시
  
```c
// Scattering 예시
MPI_Scatter(sendbuf, sendcount, MPI_INT, recvbuf, recvcount, MPI_INT, root, MPI_COMM_WORLD);

// Gathering 예시
MPI_Gather(sendbuf, sendcount, MPI_INT, recvbuf, recvcount, MPI_INT, root, MPI_COMM_WORLD);
```

---
  
## ✅ Scattering & Gathering 비교

| 항목 | Scattering | Gathering |
|------|------------|-----------|
| 목적 | 분산 처리 | 데이터 수집 |
| 방향 | 하나 → 여러 | 여러 → 하나 |
| 예시 | 웹 콘텐츠 분산 전송 | 통계 데이터 집계 |
| 활용 기술 | MPI, 분산 파일 시스템 | MapReduce, MPI |

---
  
## ✅ 실제 활용 사례

- **Scattering**:
  - CDN(Content Delivery Network)에서 사용자 위치에 따라 서버 분산
  - 병렬 계산 시 행렬의 일부를 각각의 프로세서에 분산

- **Gathering**:
  - 다수의 IoT 센서에서 중앙 서버로 데이터 수집
  - 분산 계산 결과를 하나의 마스터 노드로 집계

---
  
# 연결문서
