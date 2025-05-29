---
title : "Port Forwarding"
excerpt : "Port Forwarding"
toc : true
toc_sticky : true
toc_label : "Port Forwarding"
categories:
- ServerCommon
tags:
- [ServerCommon]
last_modified_at: 2023-11-20T08:00:00-10:00:00
---
  
---
  
## 📌 Port Forwarding이란?

> **info**
>
> **Port Forwarding**은 외부에서 특정 포트로 들어온 요청을 내부 네트워크의 다른 IP 또는 포트로 전달하는 기술이다. 주로 NAT(Network Address Translation)를 사용하는 환경에서 외부 접근을 가능하게 하기 위해 사용된다. 
{: .notice--info}  

![](98.Resources/Images/PortForwarding.png)

---
  
## ✅ 주요 기능

- 내부 네트워크에 위치한 서버/서비스를 외부에서 접근 가능하도록 함
- **NAT 방화벽**을 우회하여 통신 가능
- 원격 기기에 대한 **SSH, FTP, HTTP** 접근 가능
- 인터넷 연결 속도 개선 또는 분산 처리 구조에서 유용하게 활용

---
  
## ✅ 사용 사례

| 사례 | 설명 |
|------|------|
| 원격 데스크탑 연결 | 외부에서 내부 PC에 원격 데스크탑 연결 |
| 웹 서버 노출 | 내부에서 구동 중인 로컬 웹 서버를 외부 공개 |
| 게임 서버 호스팅 | 멀티플레이 게임의 서버 포트를 외부에 개방 |
| IoT 기기 접속 | 홈 네트워크 내 IoT 장비에 외부에서 접속 |
| Docker 컨테이너 포트 매핑 | 외부 포트를 컨테이너 내부 포트로 연결 (e.g. `-p 8080:80`) |

---
  
## ✅ 설정 방식
  
### ✳️ 공유기에서 설정 (가정/소규모 네트워크)

1. 공유기 관리자 페이지 접속
2. 포트 포워딩(또는 가상서버) 메뉴 이동
3. 내부 IP 및 포트, 외부 포트 지정
4. 적용 및 재부팅
  
### ✳️ Linux에서 iptables 사용
  
```bash
iptables -t nat -A PREROUTING -p tcp --dport 8080 -j DNAT --to-destination 192.168.0.100:80
iptables -t nat -A POSTROUTING -j MASQUERADE
```
  
### ✳️ SSH 터널링 (로컬 포트 포워딩)
  
```bash
ssh -L 8080:localhost:80 user@remote-server
```

---
  
## ✅ 유의사항

- **보안상 주의 필요**: 외부에서 포트 개방 시 불필요한 서비스 노출 가능
- **방화벽 설정 필요**: 서버 및 공유기 방화벽에서 포트 허용
- **고정 IP 또는 DDNS 사용 권장**
- **충돌 방지**: 이미 사용 중인 포트를 다시 포워딩하면 충돌 발생 가능

---
  
# 연결 문서
- [SSH](../../통신/통신-SSH)
