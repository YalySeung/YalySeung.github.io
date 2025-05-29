---
title : "DDNS"
excerpt : "DDNS"
toc : true
toc_sticky : true
toc_label : "DDNS"
categories:
- ServerCommon
tags:
- [ServerCommon]
last_modified_at: 2023-11-20T08:00:00-10:00:00
---
  
---
  
## 📌 DDNS(Dynamic DNS)란?

> **info**
>
> DDNS(Dynamic Domain Name System)는 **IP 주소가 변경될 때마다 DNS 레코드를 자동으로 업데이트하는 시스템**이다.  
> 주로 **유동 IP 환경에서도 고정된 도메인 주소를 제공**하기 위해 사용된다. 
{: .notice--info}  

---
  
## ✅ DDNS의 필요성

- 일반 가정이나 소규모 사무실은 보통 **유동 IP**를 제공받음
- IP가 바뀔 때마다 **직접 DNS 정보를 수정하는 것은 비효율적**
- **DDNS는 IP 변경을 감지하고 자동으로 DNS 서버에 반영**
- 결과적으로 사용자는 **변하지 않는 도메인 이름**으로 시스템에 접속 가능

---
  
## ✅ DDNS 동작 원리

1. 라우터 또는 클라이언트가 공인 IP 주소를 DDNS 서비스에 전달
2. DDNS 서버는 해당 IP로 DNS 레코드를 자동 갱신
3. 외부 사용자는 항상 동일한 도메인으로 접근 가능

---
  
## ✅ DDNS 사용 사례

| 용도 | 설명 |
|------|------|
| 원격 접속 | 집에 있는 NAS, CCTV 등에 고정 도메인으로 접속 |
| 소규모 서버 운영 | 자체 서버를 운영하지만 고정 IP가 없는 환경 |
| 홈 네트워크 | 외부에서 홈 네트워크 제어, IP 카메라 연결 등 |

---
  
## ✅ 대표적인 DDNS 서비스

- **No-IP (https://www.noip.com)**
- **DuckDNS (https://www.duckdns.org)**
- **DynDNS (유료, discontinued 일부 국가에서)**
- **Cloudflare API를 통한 자동 업데이트 구현도 가능**

---
  
## ✅ DDNS 설정 방법 (일반 라우터 기준)

1. DDNS 제공 사이트 가입 및 도메인 등록
2. 공유기 또는 NAS의 DDNS 메뉴에서 서비스 정보 입력
3. 공유기가 주기적으로 IP 변경 감지 → DDNS 서버에 자동 반영

---
  
## ✅ 주의 사항

- 무료 DDNS 서비스는 **주기적 갱신(30일마다 확인 등)**이 필요할 수 있음
- 방화벽 및 포트포워딩 설정도 함께 고려 필요
- 일부 ISP는 DDNS 서비스 차단 정책 존재

---
  
# 연결문서
- [DHCP](../../통신/통신-DHCP)
- [DNS](../../servercommon/servercommon-DNS)
- [Port Forwarding](../../servercommon/servercommon-Port-Forwarding)
