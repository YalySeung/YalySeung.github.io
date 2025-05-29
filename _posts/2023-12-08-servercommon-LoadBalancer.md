---
title : "LoadBalancer"
excerpt : "LoadBalancer"
toc : true
toc_sticky : true
toc_label : "LoadBalancer"
categories:
- ServerCommon
tags:
- [ServerCommon]
last_modified_at: 2023-12-08T08:00:00-10:00:00
---
  
---
  
## 📌 Load Balancer(부하 분산기)란?

> **info**
>
> Load Balancer는 클라이언트의 요청을 여러 서버로 분산하여 시스템의 **가용성, 안정성, 처리 성능**을 높여주는 네트워크 장치 또는 소프트웨어다. 
{: .notice--info}  

---
  
## ✅ 역할

- NAT(Network Address Translation)와 Load Balancing 알고리즘을 사용하여 **Client 요청을 각 서버 목적지에 고르게 분산**
- **단일 장애 지점(SPOF)** 제거 및 **트래픽 병목 최소화**
- OSI 7계층의 각 계층에서 다양한 분산 전략을 제공  
  (상위 계층 스위치는 하위 계층 기능도 포함)

---
  
## ✅ 계층별 Load Balancer 종류

| 계층 | 분산 기준 | 설명 |
|------|-----------|------|
| L2 | MAC 주소 | MAC 주소 기반의 단순 분산 |
| L3 | IP 주소 | IP 기반의 라우팅 수준 분산 |
| L4 | IP + Port | TCP, UDP 프로토콜 기반 분산 |
| L7 | HTTP 헤더, 쿠키 등 | 애플리케이션 계층 기반 분산 (ex. URL path, Host 등) |

---
  
## ✅ Load Balancing Algorithm

| 알고리즘 | 설명 |
|----------|------|
| **Round Robin** | 서버에 들어온 요청을 순서대로 돌아가며 분산. 동일 스펙 서버에 적합 |
| **Weighted Round Robin** | 서버마다 가중치를 설정하고 비율에 따라 요청 분배 |
| **IP Hash** | 클라이언트 IP를 해시하여 항상 같은 서버에 연결되도록 설정 |
| **Least Connection** | 연결 수가 가장 적은 서버에 우선 분배 |
| **Least Response Time** | 연결 수 + 응답시간을 고려하여 가장 효율적인 서버에 요청 분배 |

---
  
## ✅ L7 Load Balancer 예시

- **NGINX**
- **Apache HTTP Server (mod_proxy_balancer)**
- **AWS Application Load Balancer(ALB)**
- **HAProxy**

---
  
## ✅ 이중화 구성(HADR, HA)

- Load Balancer 자체도 단일 장애 지점이 되므로 **Active-Standby** 또는 **Active-Active** 구성 필요
- [서버 이중화](../../servercommon/servercommon-서버-이중화)와 함께 사용하는 것이 일반적

---
  
# 연결문서
- [서버 이중화](../../servercommon/servercommon-서버-이중화)
- [Proxy서버](../../webcommon/webcommon-Proxy서버)
- [TCP](../../통신/통신-TCP)
- [HTTP](../../servercommon/servercommon-HTTP)
