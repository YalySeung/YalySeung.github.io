---
title : "Web Socket"
excerpt : "Web Socket"
toc : true
toc_sticky : true
toc_label : "Web Socket"
categories:
- 통신
tags:
- [통신]
last_modified_at: 2023-10-20T08:00:00-10:00:00
---

# 날짜 : 2023-10-20 14:45

# 태그 : #통신
---

## 정의
> Web Socket이란?
>양방향 통신을 지원하는 웹 통신 프로토콜

## 특징
- 웹 브라우저와 웹서버 간의 상호작용에서 오버헤드가 낮음
- 실시간 데이터 전송 용이
- 연결을 수립하지 않고 Payload만 전송할 수 있음

## 연결 프로세스
- HTTP 프로토콜을 통해 웹 소켓 연결(Hand Shake)
- 연결이 정상적으로 이루어진 후 일정 시간이 지나면 HTTP 연결은 자동 해제

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
- [Socket](../../통신/통신-Socket)