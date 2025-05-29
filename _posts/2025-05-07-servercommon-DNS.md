---
title : "DNS"
excerpt : "DNS"
toc : true
toc_sticky : true
toc_label : "DNS"
categories:
- ServerCommon
tags:
- [통신]
last_modified_at: 2025-05-07T08:00:00-10:00:00
---
  
---
  
## 📌 DNS(Domain Name System)란?

> **info**
>
> DNS는 사람이 이해하기 쉬운 도메인 주소(예: www.google.com)를 **컴퓨터가 이해할 수 있는 IP 주소(예: 142.250.64.100)**로 변환해주는 **인터넷 전화번호부 시스템**이다. 
{: .notice--info}  

---
  
## ✅ DNS가 필요한 이유

- 기억하기 쉬운 도메인 주소 사용 가능
- IP 변경에도 도메인은 그대로 유지 → 가용성과 유연성 확보
- 전 세계에서 도메인을 통일된 방식으로 관리할 수 있음

---
  
## ✅ DNS의 계층 구조

```
Root (.)
 └── TLD (.com, .net, .org, .kr)
     └── 2차 도메인 (google, naver, etc.)
         └── 서브도메인 (www, mail, etc.)
```

예: `www.google.com`

- `.`: 루트 도메인
- `com`: 최상위 도메인 (TLD)
- `google`: 2차 도메인
- `www`: 호스트 또는 서브도메인

---
  
## ✅ DNS 동작 흐름
  
![image](../../assets/images/DNSWorkflow.png)

1. 사용자가 브라우저에 도메인 입력 (예: www.example.com)
2. 로컬 DNS 캐시 확인
3. ISP의 DNS 서버 질의
4. 루트 네임서버 → TLD 서버 → 권한 있는 네임서버로 순차 질의
5. 해당 도메인의 IP 주소 반환
6. 사용자는 해당 IP에 연결하여 웹사이트 접속

---
  
## ✅ 주요 용어

| 용어 | 설명 |
|------|------|
| **레코드(Record)** | DNS가 저장하는 정보 (예: A, CNAME 등) |
| **A 레코드** | 도메인 → IPv4 주소 매핑 |
| **AAAA 레코드** | 도메인 → IPv6 주소 매핑 |
| **CNAME 레코드** | 도메인 → 다른 도메인 매핑 |
| **MX 레코드** | 메일 서버 위치 지정 |
| **NS 레코드** | 권한 있는 네임서버 정보 |

---
  
## ✅ DNS 캐시 계층

- 브라우저 캐시
- OS 레벨 캐시
- 로컬 DNS 서버(ISP)
- 권한 네임서버

> **tip**
>
> 캐시를 통해 DNS 응답 속도를 줄이고 네트워크 부하를 최소화함. 
{: .notice--info}  

---
  
## ✅ DNS 관련 명령어
  
```bash
nslookup www.example.com      # 도메인 조회
dig www.example.com           # 자세한 쿼리 정보 확인
host www.example.com          # 간단한 도메인 해석
ipconfig /flushdns (Windows)  # DNS 캐시 초기화
```

---
  
# 연결문서
- [DDNS](../../servercommon/servercommon-DDNS)
- [DHCP](../../통신/통신-DHCP)
- [Port Forwarding](../../servercommon/servercommon-Port-Forwarding)
