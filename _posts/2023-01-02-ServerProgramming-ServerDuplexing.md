---
title: "서버 이중화"
excerpt: "서버 안정성 확보"

categories:
- ServerProgramming 

tags:
- [ServerProgramming]

toc: true
toc_sticky: true
toc_label: "서버 이중화"
last_modified_at: 2023-01-02T08:00:00-10:00:00
---

# 서버 이중화란? 
  - 서비스 안정성을 위해 각종 자원(하드웨어, OS, 미들웨어, DB등)을 이중으로 구성하는 것

---

# 목적
## 장애 또는 재해 대처(Fail Over)
  - 서비스 지속성 확보
  - 하나의 자원에 장애가 발생해도 자른 자원으로 서비스를 제공하여 사용자가 장애를 인지하지 못하도록 하기 위함

## 부하 분산(Load Balancing)
  - 하나의 자원에서 일정량 이상의 트랜잭션을 처리하는 경우 응답시간이 지연될 가능성 존재
  - 사용 트랜잭션의 패턴과 사용량을 고려하여 병렬로 요청을 처리
  - 요청과 응답이 모두 Load Balancer를 경유
  - Load Balancer의 NAT(Network Addresss Translation)를 통해 IP/MAC 주소를 변조
  - NAT : private IP를 public IP 변조하는 변조기

---

# 서버 이중화 방법
## Active-Standby  
  ![image](/assets/images/ServerProgramming/Active_Standby.png)  

  - 활성화 상태의 서버와 예비 클론 서버를 구성
  - 하나의 자원에서 장애가 발생했을 경우 예비 시스템을 가동
  - 활성화/비활성화 서버간 heartbeat를 주고받아 시스템의 정상상태를 주기적으로 체크
  - 실데이터는 실시간 동기화

## Active-Active  
  ![image](/assets/images/ServerProgramming/Active_Active.png)  
  - 두개의 자원을 활성화 상태로 운영
  - 부하 분산에 중점을 둔 이중화 방법
  - L4, L7 스위치등의 부하분산 로드밸런서를 사용

---

# Load Balancer 
  - L2, L3, L4, L7 ... 등이 있다.
  - NAT와 Load Balancing Algorithm을 사용하여, Client 요청을 각 목적지에 분산시키는 기능을 수행
  - 스위치의 각 숫자는 OSI 7 계층의 각 계층을 의미하며, 상위 스위치는 하위 스위치의 기능도 지원한다.

## L2
  - MAC 주소를 바탕으로 Load Balancing 수행

## L3
  - IP 주소를 바탕으로 Load Balancing 수행
  
## L4
  - IP와 Port 정보를 활용하여 LoadBalancing 수행
  - TCP, UDP

## L7
  - 애플리케이션 계층(HTTP, FTP, SMTP)에서 부하 분산
  - http 헤더, 쿠키 등과 같은 정보를 기준으로 트래픽 분산 가능

---

# Load Balancing Algorithm

## 라운드 로빈(Round Robin)
  - 서버에 들어온 요청을 순서대로 돌아가며 분산
  - 클라이언트 요청을 순서대로 분배하기 때문에 동일한 스펙의 자원에 적용

## 가중 라운드로빈(Weighted Round Robin)
  - 각 자원마다 가중치를 매기고 가충치가 높은 순으로 요청을 배분
  - 상이한 스펙의 자원에 사용

## IP 해시(IP Hash)
  - 클라이언트 IP 주소를 특정 자원로 매핑하여 요청을 처리
  - 사용자 IP를 해싱하여 부하를 분산하기 때문에 항상 동일한 자원에 연결

## 최소 연결 방식(Least Connection)
  - 요청이 들어온 시점에 가장 적은 연결상태를 가진 자원에 우선적으로 트래픽을 배분

## 최소 리스폰 타임(Least Response Time)
  - 자원의 현재 연결 상태와 응답시간으로 모두 고려하여 트래픽 분산
  - 가장 적은 연결상태와 가장 짧은 응답시간을 가진 자원에 우선적으로 요청 배분
