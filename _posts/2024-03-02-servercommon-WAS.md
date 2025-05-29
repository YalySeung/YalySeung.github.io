---
title : "WAS"
excerpt : "WAS"
toc : true
toc_sticky : true
toc_label : "WAS"
categories:
- ServerCommon
tags:
- [ServerCommon]
last_modified_at: 2024-03-02T08:00:00-10:00:00
---
  
---
  
## 📌 WAS(Web Application Server) 정의

> **info**
>
> WAS는 Web Application Server의 약자로, **웹 서버와 웹 컨테이너 역할을 통합한 미들웨어 소프트웨어**이다.  
> 클라이언트 요청을 처리하고, **동적인 웹 콘텐츠(JSP, Servlet 등)**를 생성하여 응답하는 핵심 서버 역할을 수행한다. 
{: .notice--info}  

---
  
## ✅ WAS 구성 요소

| 구성 요소 | 설명 |
|-----------|------|
| **Web Server** | 정적 리소스(HTML, CSS, JS 등)를 제공 |
| **Web Container (Servlet Container)** | 동적 요청(Servlet, JSP) 처리 |
| **Application Logic** | 비즈니스 로직 수행 영역 |
| **DB Connector** | 데이터베이스 연결 및 트랜잭션 처리 |

---
  
## ✅ 주요 기능

- 프로그램 실행 환경 제공 (JVM 위에서 Java 기반 앱 구동)
- 사용자 요청을 기반으로 동적 콘텐츠 생성
- DB 연결/트랜잭션 처리, 커넥션 풀 관리
- 사용자 세션, 인증/인가 관리
- WAS 자체 스케줄러, 보안 모듈, 로깅, 설정 관리 등 포함

---
  
## ✅ 동작 흐름

```
[Client]
   ↓ (HTTP 요청)
[Web Server]
   ↓ (동적 요청)
[WAS]
   ↓
[Servlet/JSP → DB 처리 → 응답]
   ↑
[Response 전송]
```

---
  
## ✅ WAS vs Web Server

| 항목 | WAS | Web Server |
|------|-----|------------|
| 콘텐츠 유형 | 동적 페이지 | 정적 페이지 |
| 예시 기술 | Tomcat, JBoss, WebLogic | Apache, Nginx |
| 스크립트 처리 | Java Servlet, JSP, Spring 등 | 없음 |
| 실행 환경 | JVM 기반 실행 | 단순 파일 제공 |

---
  
## ✅ 대표적인 WAS 제품

- **Apache Tomcat**: 가장 널리 사용되는 Java 기반 경량 WAS
- **JBoss / WildFly**: Java EE 기반 기업용 WAS
- **WebLogic**: Oracle 상용 WAS, 고성능, 안정성
- **WebSphere**: IBM WAS, 금융기관에서 많이 사용

---
  
## ✅ 확장성/이중화 구성

- 클러스터링: 세션 공유, 로드밸런싱
- Reverse Proxy 또는 L7 스위치 앞단 배치
- 서버 이중화 및 장애 대비 구조 설계 필수

---
  
# 연결문서
- [Web Service Architecture](../../servercommon/servercommon-Web-Service-Architecture)
- [Web Container](../../servercommon/servercommon-Web-Container)
- [Tomcat](../../servercommon/servercommon-Tomcat)
- [LoadBalancer](../../servercommon/servercommon-LoadBalancer)
