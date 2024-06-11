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
  
---
  
## java.io.IOException: Broken pipe
 Boken pipe 에러가 발생하는 상황은 크게 3가지가 있다.
 
 첫째,  **Receiver**가 받은 데이터를 제때 처리하지 못하는 상황(**네트워크가 느리거나 CPU 가 max **)에서 **Sender** 가 계속 Request를 보내는 경우 발생한다.
 
 둘째, **소켓을 담당하는 프로세서가 갑작스런 이상으로 종료**된 상황에서 상대 소켓은 이를 알지 못하고 데이터를 전송할 때 문제가 발생한다.
 
 셋째, 클라이언트 요청 후 서버에서 작업을 완료하여 클라이언트로 결과를 넘겨주기 전에 **네트워크가 끊김**, **클라이언트가 정지 버튼을 누름**, **브라우저를 종료**, **다른화면으로 이동** 같은 최초 요청에 대한 정보가 사라질 경우 서버 측에서 작업 결과를 전달할 곳이 없어 발생한다.
  
## 해결방법
 Broken pipe 에러에 대한 예외처리 방법은 크게 5가지 정도가 있다. 
 
 첫째, 클라이언트가 요청(Request)을 했다면 **응답(Response)이 올 때까지 대기**한다. 이 방법은 **속도가 느려질 수 있다는 단점**이 있다.
 
 둘째, **Exception을 무시**하고 넘어가는 방법이 있다. Server의 입장에서는 Client의 비정상 종료를 알 방법이 없기 때문에 상황에 따라 적절한 방법일 수 있다.

 셋째, Client의 중복 요청을 확인하여, Block하는 방법이 있다. 
 
---
  
# 연결문서
- [NIO](../../java/java-NIO)