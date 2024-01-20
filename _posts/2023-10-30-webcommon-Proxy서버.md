---
title : "Proxy서버"
excerpt : "Proxy서버"
toc : true
toc_sticky : true
toc_label : "Proxy서버"
categories:
- WebCommon
tags:
- [WebCommon]
last_modified_at: 2023-10-30T08:00:00-10:00:00
---

# 날짜 : 2023-10-30 14:44

# 태그 : #WebCommon
---

# 내용

## 정의
> **Proxy서버란?**
>
> 내부 네트워크에서 인터넷을 접속할 때, 빠른 액세스나 안전한 통신을 확보하기 위한 중계자
{: .notice--info}
- Client와 Web Server의 중간에 위치
  
![image](../../assets/images/ProxyBase.png)

## 기능
- Server IP가 아닌 Proxy IP를 노출하여 개인정보 보호
- 캐시 사용으로 속도 향상
- 로그 관리 편의성
- 허용된 IP 대역의 프록시를 사용하여 접속 우회

## 종류

### Forward Proxy
- Client 대신 Proxy가 목적 서버에 통신해주는 구성
- 요청을 중계하며 요청과 응답은 모두 Proxy를 거친다
- 클라이언트를 감추는 효과
  
![image](../../assets/images/ForwardProxy%201.png)

### Reverse Proxy
- 내부서버 대신 Proxy가 Client와 통신해주는 구성
- 응답을 중계하며 요청과 응답은 모두 Proxy를 거친다.
- 내부 서버를 감추는 효과
  
![image](../../assets/images/ReverseProxy.png)

---

# 연결문서
