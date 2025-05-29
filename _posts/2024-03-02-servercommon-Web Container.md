---
title : "Web Container"
excerpt : "Web Container"
toc : true
toc_sticky : true
toc_label : "Web Container"
categories:
- ServerCommon
tags:
- [ServerCommon]
last_modified_at: 2024-03-02T08:00:00-10:00:00
---
  
---
  
## 📌 Web Container란?

> **info**
>
> Web Container는 WAS(Web Application Server)의 핵심 구성 요소 중 하나로, **Servlet 및 JSP를 실행하고 관리하는 환경**을 제공한다.  
> 주로 Java 기반 웹 애플리케이션에서 동적인 요청 처리를 담당하며, **HTTP 요청과 Servlet 간의 연결 고리** 역할을 수행한다. 
{: .notice--info}  

---
  
## ✅ Web Container의 핵심 역할

- **Servlet 생명주기 관리**: 객체 생성 → 초기화(init) → 요청 처리(service) → 소멸(destroy)
- **HTTP 요청 분배 및 매핑 처리**: URL 기반 매핑, 필터/인터셉터 연계
- **요청/응답 객체 생성 및 전달**: `HttpServletRequest`, `HttpServletResponse`
- **web.xml 또는 애노테이션 기반 설정 처리**
- **다중 스레드 기반 동시성 처리 (Thread Pool 활용)**
- **JSP 처리 엔진 연동 및 변환(→ 서블릿) 실행**
- **보안 및 인증 처리**: 선언적 보안 (`web.xml`) 또는 프로그래밍 보안 적용

---
  
## ✅ Servlet Container vs Web Container

| 구분 | Servlet Container | Web Container |
|------|-------------------|---------------|
| 포함 범위 | Servlet 기능에 한정 | Servlet + JSP 처리 포함 |
| 용어 사용 | 동일하게 사용되는 경우 많음 | 일부 WAS 문서에서 분리하여 기술 |

---
  
## ✅ Web Container의 동작 흐름

```
[Client] → HTTP 요청 → [Web Server] → [Web Container]
 → URL 매핑 → Servlet 호출 → 응답 처리 → 결과 전송
```

- URL → Servlet 매핑은 `web.xml` 또는 `@WebServlet` 애노테이션 기반
- 요청마다 새로운 Thread가 생성되거나 풀에서 할당됨

---
  
## ✅ 대표 Web Container

| 컨테이너 | 포함 WAS | 특징 |
|----------|-----------|------|
| Catalina | Tomcat | Servlet 3.x 지원, 경량화 |
| Jetty | Jetty WAS | 내장 서버로도 활용 |
| Undertow | WildFly, JBoss | 비동기 기반 고성능 |
| Resin | Caucho | JSP 최적화 특화 |
| WebSphere WebContainer | IBM WAS | 기업용 안정성 강조 |

---
  
## ✅ Web Container 설정 요소

- `web.xml`: URL 패턴, 필터, 리스너, 보안 설정 등 정의
- 애노테이션 기반 설정: `@WebServlet`, `@WebFilter`, `@WebListener`
- ServletContext, Session 관리, 필터 체인 구성 등 다양한 웹 기능 통합

---
  
# 연결문서
- [Servlet](../../spring/spring-Servlet)
- [WAS](../../servercommon/servercommon-WAS)
- [JSP](../../jsp/jsp-JSP)
