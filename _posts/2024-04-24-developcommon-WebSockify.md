---
title : "WebSockify"
excerpt : "WebSockify"
toc : true
toc_sticky : true
toc_label : "WebSockify"
categories:
- DevelopCommon
tags:
- [DevelopCommon]
last_modified_at: 2024-04-24T08:00:00-10:00:00
---
  
---
  
## 정의
> **Websockify란?**  
>
> WebSocket 프로토콜을 사용하여 TCP 및 SSL 연결을 WebSocket으로 프록시 하는 도구 
{: .notice--info}  
  
## 주요 기능
  
### Proxy 기능
- TCP 또는 SSL 트래픽을 WebSocket으로 변환하여 다른 호스트 또는 포트로 전달
- 기존의 TCP 또는 SSL 서비스를 WebSocket을 지원하는 클라이언트와 통신할 수 있도록 만듦
  
### WebSocket 지원
- TCP 또는 SSL 서비스를 웹 소켓을 지원하는 서비스로 변환하여 웹 애플리케이션과 통합
  
### SSL 확장
- HTTPS 서비스를 WebSocket을 지원하는 서비스로 변환
  
### 다중 플랫폼 지원
- 여러 플랫폼에서 실행 가능 하며, Window 애플리케이션으로도 제공됨
- Window 환경에서도 웹소켓 프록시 서버를 쉽게 설정하고 사용 가능

> **caution**
>
> websockify는 TCP 연결이기때문에 1:1 연결만 가능하다. 
{: .notice--info}  

---
  
# 연결문서
- [WebSocket](../../통신/통신-WebSocket)
- [Proxy서버](../../webcommon/webcommon-Proxy서버)