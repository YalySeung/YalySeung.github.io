---
title : "AJP"
excerpt : "AJP"
toc : true
toc_sticky : true
toc_label : "AJP"
categories:
- ServerCommon
tags:
- [ServerCommon]
last_modified_at: 2023-11-29T08:00:00-10:00:00
---
  
---
  
> **AJP란?**  
>
> Apache JServ Protocol의 약어로 웹서버 뒤에 있는 애플리케이션 서버로부터 웹서버로 들어오는 요청을 위임할 수 있는 바이너리 프로토콜이다. 
{: .notice--info}  

 AJP는 애플리케이션 서버로 핑을 할 수 있는 웹서버의 모니터링 기능 지원한다. 또한 Load Balance(부하분산) 기능 구현에 사용되며, 각 세션들을 리다이렉트 하는 기능이 있다.
  
## Apach 와 Tomcat
  
### 연동해야 하는 이유
- Tomcat은 WAS 서버이지만 Web 서버의 기능도 갖추고 있음
- Tomcat의 WAS는 Apach보다 느린 처리속도를 가지고 있음
- 정적 페이지는 Apach, 동적 페이지는 Tomcat이 처리하여 부하를 분산
- 현재는 Tomcat이 Apach에 뒤쳐지지 않을 많큼 개선되었지만 Apach 내에서만 설정할 수 있는 부분, 유용한 모듈을 사용하기 위해서 과거 방식을 사용
  
### mod_jk
> **mod_jk란?**  
>
>Apach와 Tomcat을 연결하는 모듈 
{: .notice--info}  
  
#### 특징
- AJP 프로토콜 사용
- Tomcat의 일부로 배포
- **Apach 웹서버에 설치해야 함**
  
#### 동작방식
1. Apach 웹서버의 httpd.conf에 Tomcat 연동을 위한 설정을 추가하고 Tomcat에서 처리할 요청을 지정
2. 사용자의 브라우저는 아파치 웹서버(80 port)에 접속해 요청
3. Apach 웹서버는 사용자의 요청이 Tomcat에서 처리되도록 지정된 요청인지 확인
4. Tomcat에서 처리해야 하는 경우 AJP포트(8009 port)에 접속해 요청을 전달
5. Tomcat은 Apach 웹서버로부터 요청을 받아 처리 후, 처리 결과를 Apach 웹서버에 되돌려줌
6. Apach 웹서버는 톰캣으로부터 받을 결과를 사용자에게 전송 
  
---
  
# 연결문서
- [Port](../../developcommon/developcommon-Port)