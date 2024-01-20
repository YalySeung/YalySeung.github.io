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

# 날짜 : 2023-10-20 14:45

# 태그 : #통신 #ServerCommon
---

# 내용

## 정의
> **WebSocket이란?**
>
> 서버와 클라이언트 간 양방향 데이터 전송이 가능하도록 하는 통신방법 중 하나
{: .notice--info}

## 특징
- Stateful Protocol
- 웹소켓을 위한 별도 포트는 없고 기존 포트 사용
- 프로그램으로 구성된 메시지라는 논리적 단위로 송수신
- 텍스트와 바이너리만 전송 가능
- 웹 브라우저와 웹서버 간의 상호작용에서 오버헤드가 낮음
- 실시간 데이터 전송 용이

## 동작방식
  
![image](../../assets/images/WebSocketProcess.png)
- 연결 설정을 위한 handshake(HTTP), 일정 시간 경과 후 HTTP 연결은 끊어짐
- 설정된 연결은 열린 상태로 유지(TCP/IP 기반), 클라이언트나 서버가 종료될 때까지 동일 채널에서 통신 수행
- 양방향 통신
- Cleint 또는 Server에서 Close 요청시, Disconnet

## 문제점

### 복잡성
- Stateful protocol 이기 때문에 서버와 클라이언트간 연결을 항상 유지해야 함
- 비정상적 연결 종료시, 예외처리 코드 필요

### 비용
- Socket 연결을 유지하는 데 비용 발생
- 트래픽이 많은 경우 서버 CPU에 큰 부담

### 호환성
- 오래된 버전의 웹 브라우저에서는 지원되지 않음

## Reference
- SNS
- 멀티 플레이어 Game
- 위치 기반 APP
- HTS
- 화상 채팅 APP

---

# 연결문서
- [HTTP](../../servercommon/servercommon-HTTP)