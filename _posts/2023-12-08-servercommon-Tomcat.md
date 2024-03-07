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

# 날짜 : 2023-12-08 15:37

# 태그 : #ServerCommon
---

# 내용

## 정의
> **Tomcat이란?**
>
> Java Servlet을 실행하고 웹페이지를 렌더링하는 응용프로그램 서버
{: .notice--info}

## 주요 모듈

### Catalina
- Tomcat의 핵심 Container 역할을 담당
- Servlet Container, JSP Container, Web Application 실행을 관리

### Coyote
- HTTP 요청을 Catalina에 전달
- HTTP/1.1, HTTP/2 프로토콜 지원

### Jasper
- JSP 페이지를 컴파일하고 실행하는 Tomcat의 JSP 엔진
- JSP 페이지를 java Sevlet 클래스로 변환하여 실행

### Cluster
- Tomcat Clustering 지원
- 여러 대의 Tomcat 서버를 하나의 논리적인 그룹으로 묶어 로드 밸런싱과 고가용성 제공

### Juli
- Tomcat의 로깅 시스템

### Security
- Tomcat의 보안 담당
- SSL/TLS 지원
- 사용자 인증 및 권한 부여, 디지털 서명 및 암호화 기능 제공

### Resources
- Tomcat의 리소스 관리 담당
- DB Connection Pool, JNDI 리소스, 파일시스템 리소스를 관리하고 제공

### Naming
- JNDI를 사용하여 java Application의 리소스 검색 및 엑세스

### WebSocket
- Tomcat에서 WebSocket 프로토콜 지원
- 클라이언트와 서버간 양방향 통신 지원

### Manager
- Tomcat의 Web Application 관리
- Web Application의 배포, 시작, 정지, 재시작을 관리

---

# 연결문서
- [Tomcat 설정](../../servercommon/servercommon-Tomcat-설정)