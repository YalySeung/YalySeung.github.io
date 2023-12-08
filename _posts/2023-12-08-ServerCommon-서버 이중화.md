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

# 날짜 : 2023-12-08 16:06

# 태그 : #ServerCommon 
---

# 내용

## 정의
> 서버 이중화란?
> 서비스 안정성을 위해 각종 자원(하드웨어, OS, 미들웨어, DB등)을 이중으로 구성하는 것  

## 목적

### 장애 또는 재해 대처(Fail Over)
- 서비스 지속성 확보
- 하나의 자원에 장애가 발생해도 자른 자원으로 서비스를 제공하여 사용자가 장애를 인지하지 못하도록 하기 위함

### 부하 분산(Load Balancing)
- 하나의 자원에서 일정량 이상의 트랜잭션을 처리하는 경우 응답시간이 지연될 가능성 존재
- 사용 트랜잭션의 패턴과 사용량을 고려하여 병렬로 요청을 처리
- 요청과 응답이 모두 Load Balancer를 경유
- Load Balancer의 NAT(Network Addresss Translation)를 통해 IP/MAC 주소를 변조
- NAT : private IP를 public IP 변조하는 변조기

## 서버 이중화 방법

### Active-Standby  
![image](./../../assets/images/Active_Standby.png) 
- 활성화 상태의 서버와 예비 클론 서버를 구성
- 하나의 자원에서 장애가 발생했을 경우 예비 시스템을 가동
- 활성화/비활성화 서버간 heartbeat를 주고받아 시스템의 정상상태를 주기적으로 체크
- 실데이터는 실시간 동기화

### Active-Active  
![image](./../../assets/images/Active_Active.png)
- 두개의 자원을 활성화 상태로 운영
- 부하 분산에 중점을 둔 이중화 방법
- L4, L7 스위치등의 부하분산 로드밸런서를 사용
  
---

# 연결문서
- [LoadBalancer](../../ServerCommon/ServerCommon-LoadBalancer)