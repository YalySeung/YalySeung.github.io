---
title : "Tomcat"
excerpt : "Tomcat"
toc : true
toc_sticky : true
toc_label : "Tomcat"
categories:
- ServerCommon
tags:
- [ServerCommon]
last_modified_at: 2023-12-08T08:00:00-10:00:00
---
  
---
  
## 📌 정의

> **info**
>
> Tomcat은 Java Servlet 및 JSP(JavaServer Pages)를 실행하기 위한 **오픈소스 웹 애플리케이션 서버**이며, **Apache Software Foundation**에서 개발 및 유지되고 있다.  
> 주로 Java 기반 웹 프로젝트의 실행 환경으로 사용된다. 
{: .notice--info}  

---
  
## ✅ Tomcat 주요 모듈

| 모듈 | 설명 |
|------|------|
| **Catalina** | Tomcat의 핵심 Servlet Container로서 요청 처리 및 서블릿 생명주기 관리 |
| **Coyote** | HTTP 커넥터 역할을 하며, 외부 요청을 Catalina로 전달 |
| **Jasper** | JSP 파일을 서블릿으로 변환하고 실행하는 엔진 |
| **Cluster** | 로드밸런싱 및 고가용성을 위한 클러스터링 기능 제공 |
| **Juli** | Tomcat 자체 로깅 시스템 |
| **Security** | SSL, 인증, 권한 부여 등 보안 기능 담당 |
| **Resources** | DB Connection Pool, JNDI 리소스 등 관리 |
| **Naming** | JNDI를 통해 리소스 검색 및 접근 지원 |
| **WebSocket** | 웹소켓 기반 실시간 양방향 통신 지원 |
| **Manager** | WAR 배포, 애플리케이션 시작/정지 등을 웹 UI로 제어 가능 |

---
  
## ✅ Tomcat 주요 특징

- Servlet과 JSP 표준 구현체 제공
- Lightweight한 구조 → 개발 및 테스트용으로 적합
- Apache HTTP Server와 연동 시 정적 리소스 처리 최적화 가능
- 다양한 OS에서 실행 가능 (Windows, Linux, macOS 등)
- WebSocket, SSL/TLS, JNDI, clustering 등 풍부한 기능 제공

---
  
## ✅ Tomcat 구조 요약

```
┌────────────┐
│   Coyote   │ ← HTTP 요청 수신
└────┬───────┘
     ▼
┌────────────┐
│  Catalina  │ ← 요청 처리 및 Servlet/JSP 실행
└────┬───────┘
     ▼
┌────────────┐
│  Jasper    │ ← JSP를 서블릿으로 변환하여 실행
└────────────┘
```

---
  
## ✅ 배포 및 운영 팁

- WAR 파일 단위 배포: `webapps/` 폴더에 복사
- `/conf/server.xml`로 포트, 호스트, SSL 설정
- `/conf/context.xml` 또는 개별 앱의 `META-INF/context.xml`로 JNDI 설정
- 로그: `logs/` 폴더 확인, Juli 기반 로깅 설정 가능

---
  
## ✅ 관리자 UI

- `/manager/html` URL에서 애플리케이션 관리
- 사용자 계정 설정: `/conf/tomcat-users.xml`
- 권한 설정 예시:
  
```xml
<role rolename="manager-gui"/>
<user username="admin" password="admin" roles="manager-gui"/>
```

---
  
# 연결문서
- [Tomcat 설정](../../servercommon/servercommon-Tomcat-설정)
- [Tomcat-logging](../../servercommon/servercommon-Tomcat-logging)
- [WebSocket](../../통신/통신-WebSocket)
- [Proxy서버](../../webcommon/webcommon-Proxy서버)
