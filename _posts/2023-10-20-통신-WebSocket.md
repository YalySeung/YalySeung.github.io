---
title : "WebSocket"
excerpt : "WebSocket"
toc : true
toc_sticky : true
toc_label : "WebSocket"
categories:
- 통신
tags:
- [통신, ServerCommon]
last_modified_at: 2023-10-20T08:00:00-10:00:00
---
  
---
  
> **WebSocket이란?**  
>
> 서버와 클라이언트 간 양방향 데이터 전송이 가능하도록 하는 통신방법 중 하나이다. 
{: .notice--info}  

 WebSocket은 **Stateful Protocol**이며, 프로그램으로 구성된 **메시지라는 논리적 단위로 송수신**한다. 웹 브라우저와 웹 서버 간의 상호작용에서 **오버헤드가 낮아 실시간 데이터 전송에 용이**하다. 반면 텍스트와 **바이너리만 전송가능하다**는 단점이 있다.
  
## WebSocket 동작 방식
  
![image](../../assets/images/WebSocketProcess.png)
 WebSocket은 최초에 연결 설정을 위한 **handshake(HTTP) 통신** 후 **TCP 채널의 연결이 유지**되고, **HTTP 연결은 끊어진다**. 설정된 연결은 열린 상태로 유지(TCP/IP 기반)되며,  클라이언트나 서버가 종료될 때까지 동일 채널에서 통신을 수행한다. Client, Server 간 **양방향 통신이 가능한 상태가 유지**되고, Client 또는 Server가 **Close 요청시, Disconnect**된다.
  
## WebSocket의 문제점
 WebSocket은 Stateful protocol이기 때문에 **Server와 Client간 연결을 항상 유지**해야한다. 이에 따른 문제점이 몇 가지 있는데, 첫째는 **비정상적 연결 종료에 대한 예외처리 코드가 필요**하다는 점이다.  TCP 소켓 통신을 하기때문에 비정상 연결 종료시, port가 제대로 close 되지 않을 수 있다. 둘째는 **Socket 연결을 유지하는 비용 문제**이다. WebSocket을 사용하는데, Traffic이 많이 발생하는 경우에 CPU에 큰 부담이 생길 수 있다. 마지막으로 **오래된 버전의 웹 브라우저와 호환이 되지 않는다**는 문제점이 있다.
  
## WebSocket을 사용하는 상용 Application
  WebSocket을 사용하는 상용 Application은 대표적으로 **Slack**, **Discord**, **GoogleDocs**, **FaceBook Messenger** 등이 있다.

---
  
# 연결문서
- [HTTP](../../servercommon/servercommon-HTTP)