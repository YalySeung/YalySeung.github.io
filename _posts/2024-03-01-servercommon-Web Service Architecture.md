---
title : "Web Service Architecture"
excerpt : "Web Service Architecture"
toc : true
toc_sticky : true
toc_label : "Web Service Architecture"
categories:
- ServerCommon
tags:
- [ServerCommon]
last_modified_at: 2024-03-01T08:00:00-10:00:00
---
  
---
  
## Web Service Architecture
  
![image](../../assets/images/RequestProcesssingProcess.png)
  
### Client
- 웹 서비스를 요청하는 사용자
  
### WebServer 
- Client로 부터 HTTP 요청을 받아들이고 HTML 문서같은 정적 컨텐츠(HTML 문서, CSS, javascript, 이미지, 파일)를 반환하는 서버
- ex) Apache, IIS, Nginx, WebtoB ...
  
### WAS
- WebServer와 Web Container가 합쳐진 형태로, WebServer 단독으로 처리할 수 없는 데이터베이스 조회 및 다양한 로직 처리가 필요한 동적 컨텐츠 제공
- Servlet Container 를 제공해주기 때문에 Web Container 혹은 Servlet Container라고 불림
- ex) Tomcat, WebLogic, WebSphere, Jeus, JBoss ...
  
### Server Architecture 종류
- User-WebServer-DB
- User-WAS-DB
- User-WebServer-WAS-DB 

> **tip**
>
> WAS가 WebServer의 역할을 함께 수행할 수 있음에도 WebServer와 같이 사용하는 이유는 WAS의 부담을 줄이고, 환경 설정 파일을 외부에 노출시키지 않도록 하기 위함이다. 
{: .notice--primary}  

---
  
# 연결문서
- [WebServer](../../servercommon/servercommon-WebServer)
- [WAS](../../servercommon/servercommon-WAS)