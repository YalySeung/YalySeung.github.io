---
title : "DMZ"
excerpt : "DMZ"
toc : true
toc_sticky : true
toc_label : "DMZ"
categories:
- ServerCommon
tags:
- [ServerCommon]
last_modified_at: 2024-10-17T08:00:00-10:00:00
---
  
---
  
> **DMZ란?**  
>
> DeMilitarized Zone 의 약어로 네트워크 비무장 지대를 의미한다.  
> 외부 네트워크와 내부 네트워크 사이에서 외부 네트워크 서비스를 제공하며 내부 네트워크를 보호하는 서브넷이다. 
{: .notice--info}  
  
## DMZ의 주요 특징
- **공격으로부터 내부 네트워크를 보호**하는 중간 방어 계층 역할
- 웹 서버, 메일 서버, DNS 서버 등 **외부 접근이 필요한 서비스를 배치**  
- **방화벽(Firewall)과 함께 설정**하여 네트워크 보안을 강화  
- **내부 네트워크와 직접적인 연결을 차단**하여 보안 사고 예방
  
## DMZ의 일반적인 구성 방식
  DMZ는 **두 개의 방화벽(Firewall)** 사이에 위치하여 외부와 내부 네트워크를 분리한다.
  
```plaintext
[인터넷] --- [방화벽] --- [DMZ] --- [방화벽] --- [내부 네트워크]
```

1. **첫 번째 방화벽** → 외부에서 DMZ로의 접근을 제한  
2. **DMZ 내부** → 웹 서버, 메일 서버, DNS 서버 등 배치  
3. **두 번째 방화벽** → DMZ에서 내부 네트워크로의 접근을 통제  
  
## DMZ의 장점과 단점
  
### ✅ 장점
- **공격이 내부 네트워크까지 확산되는 것을 방지**  
- **외부 서비스(웹 서버 등)를 안전하게 운영 가능**  
- **보안 정책을 보다 세분화하여 적용 가능**  
  
### ❌ 단점
- **설정이 잘못되면 내부 네트워크까지 위험해질 수 있음**  
- **추가적인 하드웨어(방화벽 등) 비용이 발생**  
- **운영 및 유지보수 관리가 필요**  
  
## DMZ 활용 사례
- **웹 서버 및 API 게이트웨이 운영** → 웹 서비스의 보안 강화  
- **이메일 서버 보호** → 내부 네트워크와 분리하여 보안 유지  
- **데이터베이스 서버와 분리** → 내부 데이터 보호를 위해 DMZ 외부 배치 금지  

---
  
# 연결문서