---
title : "WebServer"
excerpt : "WebServer"
toc : true
toc_sticky : true
toc_label : "WebServer"
categories:
- ServerCommon
tags:
- [ServerCommon]
last_modified_at: 2024-02-29T08:00:00-10:00:00
---
  
---
  
## 📌 정의

> **info**
>
> **Web Server**는 클라이언트(브라우저)로부터 HTTP 요청을 받아  
> **HTML, CSS, JS, 이미지 등 정적인 리소스**를 반환하는 소프트웨어 또는 하드웨어를 의미한다. 
{: .notice--info}  

---
  
## ✅ 소프트웨어적 정의

> **Web Server 소프트웨어란?**  
>
> HTTP 프로토콜을 기반으로 클라이언트 요청을 처리하고, 정적 웹 리소스를 응답하는 컴퓨터 프로그램이다. 
{: .notice--info}  

- 정적 콘텐츠 중심 (HTML, CSS, JS, 이미지)
- 대표 제품: Apache, Nginx, Microsoft IIS, WebtoB

---
  
## ✅ 하드웨어적 정의

> **Web Server 하드웨어란?**  
>
> 웹 서버 소프트웨어와 함께 웹 콘텐츠를 저장하고 서비스하는 **물리 서버 또는 가상 서버**를 의미한다. 
{: .notice--info}  

- 웹 애플리케이션 파일이 저장된 호스트
- 웹 트래픽 처리용 인프라 자원 (CPU, RAM, Storage 등 포함)

---
  
## ✅ 웹 서버의 주요 기능

| 기능 | 설명 |
|------|------|
| HTTP/HTTPS 지원 | 웹 요청 및 보안 통신 처리 |
| 정적 콘텐츠 제공 | HTML, 이미지, JS, CSS 등 반환 |
| 로깅 및 통계 | 접근 로그 기록 및 분석 도구 연동 |
| 인증 처리 | 접근 제어 및 사용자 인증 기능 제공 |
| 콘텐츠 압축 | Gzip 등으로 데이터 전송 최적화 |
| 가상 호스팅 | 하나의 서버에서 여러 도메인 서비스 |
| 대역폭 스로틀링 | 특정 요청/클라이언트에 대한 대역폭 제한 |
| 대용량 파일 지원 | 스트리밍 또는 청크 전송 방식 처리 |

---
  
## ✅ Web Server vs WAS

| 항목 | Web Server | WAS |
|------|------------|-----|
| 처리 역할 | 정적 콘텐츠 제공 | 동적 콘텐츠 처리 |
| 처리 속도 | 빠름 (캐싱, 압축 등) | 상대적으로 느림 |
| 예시 | Apache, Nginx | Tomcat, JBoss, WebLogic |
| 구동 환경 | OS에서 직접 실행 | JVM에서 동작 (Java 기반) |
| 실행 대상 | HTML, JS, 이미지 등 | Servlet, JSP 등 Java 코드 |

---
  
## ✅ Reverse Proxy 연계

- Web Server는 WAS 앞단에서 **Reverse Proxy**로도 사용됨
- 보안, 로드밸런싱, 캐싱 등을 제공하여 **WAS 부하 분산 및 보호**
- 예: `Nginx → Tomcat`, `Apache → WebLogic`

---
  
# 연결문서
- [Web Service Architecture](../../servercommon/servercommon-Web-Service-Architecture)
- [WAS](../../servercommon/servercommon-WAS)
- [Proxy서버](../../webcommon/webcommon-Proxy서버)
- [Nginx](../../servercommon/servercommon-Nginx)
- [ApacheAndTomcat](../../servercommon/servercommon-ApacheAndTomcat)
