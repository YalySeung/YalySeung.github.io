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
  
## 정의
> **Web Container란?**  
>
> 웹 서버의 컴포넌트 중 하나
> Java Servlet 과 상호작용 하는 WAS의 구성요소 
{: .notice--info}  
  
## 기능
- [Servlet](../../spring/spring-Servlet) 생명주기 관리
- 웹 서버로부터 받은 요청을 분석하여 [Servlet](../../spring/spring-Servlet) 실행, [Servlet](../../spring/spring-Servlet)이 웹서버의 정보를 확인할 수 있는 기능 제공
- multi threading 지원
- web.xml 을 통해 선언적 보안 관리 가능
- JSP 지원

> **tip**
>
> WAS 별로 다양한 컨테이너를 내장하고 있으며, 이중 Servlet 관련 기능들을 모아놓은 컨테이너의 집합을 Servlet Container라고 한다. 
{: .notice--info}  

---
  
# 연결문서
- [Servlet](../../spring/spring-Servlet)