---
title : "ApacheAndTomcat"
excerpt : "ApacheAndTomcat"
toc : true
toc_sticky : true
toc_label : "ApacheAndTomcat"
categories:
- ServerCommon
tags:
- [ServerCommon]
last_modified_at: 2024-06-11T08:00:00-10:00:00
---
  
---
  
 이 글에서는 **Apache HTTP Server(Apache)**와 **Apache Tomcat**을 비교분석 해볼 것이다.

 **Apache HTTP Server**와 **Apache Tomcat**은 모두 Apache Software Foundation에서 개발된 **웹 서버 소프트웨어**이지만, 그 용도와 기능에 있어 차이가 있다. 각 소프트웨어의 특징에 대해서 살펴보자.

---
  
## ✅ Apache HTTP Server(Apache)

> **info**
>
> 정적 파일(html, css, js 등)을 빠르게 서빙하며, 리버스 프록시 기능도 수행 가능한 범용 웹 서버 
{: .notice--info}  

- **정적 콘텐츠 제공에 최적화**
- **확장 가능한 모듈 아키텍처**: `mod_rewrite`, `mod_ssl`, `mod_proxy` 등
- **AJP 또는 HTTP를 통한 WAS 연동 가능**
- **리버스 프록시 역할 수행 가능** (예: Tomcat 앞단에 위치)

---
  
## ✅ Apache Tomcat

> **info**
>
> Java Servlet과 JSP를 실행하는 서블릿 컨테이너로, 동적 웹 애플리케이션 실행이 주 목적이다. 
{: .notice--info}  

- **Java 기반 WAS (Web Application Server)**
- **동적 콘텐츠 처리 가능** (서블릿, JSP)
- **정적 파일도 제공 가능**하지만 Apache에 비해 성능은 떨어질 수 있음
- **WAR 배포 구조**로 웹 애플리케이션 패키징

---
  
## ✅ Apache vs Tomcat 비교

| 항목          | Apache HTTP Server         | Apache Tomcat               |
|---------------|-----------------------------|-----------------------------|
| 용도          | 정적 콘텐츠 서빙              | 동적 콘텐츠 처리 (서블릿, JSP) |
| 실행 환경     | HTML, CSS, JS               | Java 기반 웹 앱(WAR)       |
| 처리 성능     | 정적 콘텐츠에 최적화           | 동적 콘텐츠 중심            |
| 모듈 기능     | 다양한 Apache 모듈 지원       | 서블릿 컨테이너 기능 중심     |
| 프록시 기능   | mod_proxy / mod_jk 등으로 가능 | 자체 처리 위주 (Apache 연동 多) |

---
  
## ✅ 통합 사용 방식
  
### 🔹 전통적 구조 (Apache + Tomcat)

- 정적 요청은 Apache에서 처리
- 동적 요청은 AJP 또는 mod_proxy를 통해 Tomcat으로 전달
- 로드밸런서 및 SSL 처리도 Apache에서 수행 가능
  
### 🔹 단독 사용 구조 (Tomcat)

- Tomcat이 정적/동적 요청을 모두 처리
- 구성 간편, 경량화된 시스템에 적합

> **tip**
>
> 복잡한 트래픽 분산이나 인증처리가 필요하다면 Apache와 Tomcat을 함께 구성하는 것이 좋다. 
{: .notice--info}  

---
  
# 연결문서
- [AJP](../../servercommon/servercommon-AJP)
- [Proxy서버](../../webcommon/webcommon-Proxy서버)
- [WAS](../../servercommon/servercommon-WAS)
- [Servlet](../../spring/spring-Servlet)
