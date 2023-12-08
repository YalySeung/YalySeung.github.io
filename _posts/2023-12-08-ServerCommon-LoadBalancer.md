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

# 날짜 : 2023-12-08 16:08

# 태그 : #ServerCommon 
---

# 내용

## 역할
- NAT와 Load Balancing Algorithm을 사용하여, Client 요청을 각 목적지에 분산시키는 기능을 수행
- 스위치의 각 숫자는 OSI 7 계층의 각 계층을 의미하며, 상위 스위치는 하위 스위치의 기능도 지원한다.

## 종류

### L2
- MAC 주소를 바탕으로 Load Balancing 수행

### L3
- IP 주소를 바탕으로 Load Balancing 수행

### L4
- IP와 Port 정보를 활용하여 LoadBalancing 수행
- TCP, UDP

### L7
- 애플리케이션 계층(HTTP, FTP, SMTP)에서 부하 분산
- http 헤더, 쿠키 등과 같은 정보를 기준으로 트래픽 분산 가능

## Load Balancing Algorithm

### 라운드 로빈(Round Robin)
- 서버에 들어온 요청을 순서대로 돌아가며 분산
- 클라이언트 요청을 순서대로 분배하기 때문에 동일한 스펙의 자원에 적용

### 가중 라운드로빈(Weighted Round Robin)
- 각 자원마다 가중치를 매기고 가충치가 높은 순으로 요청을 배분
- 상이한 스펙의 자원에 사용

### IP 해시(IP Hash)
- 클라이언트 IP 주소를 특정 자원로 매핑하여 요청을 처리
- 사용자 IP를 해싱하여 부하를 분산하기 때문에 항상 동일한 자원에 연결

### 최소 연결 방식(Least Connection)
- 요청이 들어온 시점에 가장 적은 연결상태를 가진 자원에 우선적으로 트래픽을 배분

### 최소 리스폰 타임(Least Response Time)
- 자원의 현재 연결 상태와 응답시간으로 모두 고려하여 트래픽 분산
- 가장 적은 연결상태와 가장 짧은 응답시간을 가진 자원에 우선적으로 요청 배분

---

# 연결문서
- [서버 이중화](../../ServerCommon/ServerCommon-서버-이중화)