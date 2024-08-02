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

 AJP는 주로 Apache HTTP Server와 Apache Tomcat 같은 **서블릿 컨테이너 간의 연결을 위해 사용**된다. 뿐만 아니라 **HTTP 프로토콜을 최적화**하여 더 효율적인 데이터 전송을 가능하게 돕는다.
  
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
- [ApacheAndTomcat](../../servercommon/servercommon-ApacheAndTomcat)