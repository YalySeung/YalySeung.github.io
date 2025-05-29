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
  
## 📌 Web Service Architecture란?

> **info**
>
> Web Service Architecture는 웹 서비스가 클라이언트 요청을 처리하고 응답하는 일련의 구조 및 구성 요소를 설명하는 아키텍처이다.  
> 정적 자원 제공과 동적 처리 로직을 분리하여, 효율적이고 확장 가능한 웹 서비스를 설계할 수 있도록 한다. 
{: .notice--info}  

---
  
## ✅ 구성 요소
  
![image](../../assets/images/RequestProcesssingProcess.png)
  
### 🔹 Client
- 웹 서비스를 요청하는 사용자
- 보통 브라우저 또는 API 호출기(예: Postman, 모바일 앱 등)

---
  
### 🔹 Web Server

- 클라이언트로부터 HTTP 요청을 받아들임
- 정적 콘텐츠 (HTML, CSS, JS, 이미지 등)를 반환
- 동적 요청은 WAS로 전달 (리버스 프록시 또는 커넥터 역할)
- 예: Apache, Nginx, IIS, WebtoB 등

---
  
### 🔹 WAS (Web Application Server)

- 동적 콘텐츠 생성 및 비즈니스 로직 처리 담당
- DB 접근, 트랜잭션 처리, 세션 관리 등의 역할 수행
- Servlet Container(Web Container) 포함
- 예: Tomcat, WebLogic, WebSphere, JBoss, Jeus

> **note**
>
> WAS는 Web Server의 기능을 포함하므로 단독 사용 가능하지만,  
> 보안, 성능 분산, 설정 격리를 위해 Web Server와 함께 구성하는 것이 일반적이다. 
{: .notice--info}  

---
  
## ✅ Server Architecture 패턴

| 패턴 | 설명 |
|------|------|
| User → Web Server → DB | 정적 콘텐츠 위주 아키텍처 |
| User → WAS → DB | 단순 WAS 기반 동적 처리 |
| User → Web Server → WAS → DB | 가장 일반적, 확장성/보안 최적 |

---
  
## ✅ 대표 처리 흐름 (일반적 구조)

```
Client
  ↓
[Web Server]
  ↓ 정적 자원이면 응답 반환
  ↓ 동적 요청이면
[WAS (Web Container)]
  ↓
[Servlet/JSP 실행 → DB 접근 → 응답 생성]
  ↓
Web Server → Client
```

---
  
## ✅ 아키텍처 구성 이유

- 정적/동적 콘텐츠 분리로 **리소스 효율성** 확보
- Web Server는 정적 리소스를 빠르게 제공 → WAS 부하 분산
- Web Server 외부 노출, WAS는 내부망 구성 → **보안 강화**
- 유지보수성과 확장성이 뛰어난 모듈형 구조

---
  
# 연결문서
- [WebServer](../../servercommon/servercommon-WebServer)
- [WAS](../../servercommon/servercommon-WAS)
- [Web Container](../../servercommon/servercommon-Web-Container)
- [Proxy서버](../../webcommon/webcommon-Proxy서버)
