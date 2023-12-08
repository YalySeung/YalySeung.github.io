---
title : "java.io.IOException"
excerpt : "java.io.IOException"
toc : true
toc_sticky : true
toc_label : "java.io.IOException"
categories:
- Exception
tags:
- [Spring, Exception, java]
last_modified_at: 2023-11-23T08:00:00-10:00:00
---

# 날짜 : 2023-11-23 16:04

# 태그 : #Spring #Exception #java 
---

# 내용

## 상세 타입 별 분석

### : Broken pipe

#### 원인
- **Receiver** 에서 송신 받은 데이터를 제때 처리하지 못하는 상황(네트워크가 느리거나 CPU 가 max 인 경우)에서 **Sender** 가 계속 보내는 경우 발생한다.
- 2개의 소켓상의 통신에서 소켓을 담당하던 프로세서가 갑작스런 이상으로 종료된 상황에서 상대 소켓은 이를 알지 못하고 데이터를 전송할 때 문제가 발생한다.
- 클라이언트 요청 후 서버에서 작업을 완료하여 클라이언트로 결과를 넘겨주기 전에 **네트워크가 끊김, 클라이언트가 정지 버튼을 누름, 브라우저를 종료, 다른화면으로 이동** 같은 최초 요청에 대한 정보가 사라질 경우 서버 측에서 작업 결과를 전달할 곳이 없어 발생한다.

#### 해결방법
- 클라이언트가 요청(Request)을 했다면 응답(Response)이 올 때까지 대기 
- Exception 무시
- 중복 요청 확인 후 Block
- Timeout값을 늘리기
- 가용 스레드 늘리기

---

# 연결문서
- [NIO](../../java/java-NIO)