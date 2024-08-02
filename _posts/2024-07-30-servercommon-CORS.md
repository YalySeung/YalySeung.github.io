---
title : "CORS"
excerpt : "CORS"
toc : true
toc_sticky : true
toc_label : "CORS"
categories:
- ServerCommon
tags:
- [ServerCommon, 미완료]
last_modified_at: 2024-07-30T08:00:00-10:00:00
---
  
---
  
 Local PC에서 SpringBoot Backend 서버와 React Frontend를 연동하던 중 CORS 에러와 마주했다. 이 글에서는 CORS 가 무엇인지, 에러를 어떻게 해결하는지에 대해서 다룰 것이다.

> **CORS 란?**  
>
> Cross-Origin Resource Sharing의 약어로 웹 애플리케이션이 다른 출처의 서버에 리소스를 요청할 때 발생하는 보안 정책을 정의한다. 
{: .notice--info}  

 CORS를 검색하면 출처 라는 용어가 많이 등장하는데 이 출처란 무엇인지 먼저 알아보자. 

 **출처**는 프로토콜, 도메인, 포트로 구성된다. 이중 하나라도 다르면 다른 출처라고 볼 수 있다. 예를 들어, http://mydomain.com 에서 http://yourdomain.com 으로 리소스를 요청하는 행위는 다른 출처로 요청을 보내는 것이며, 이를 **크로스 오리진** 요청이라고 한다.

 CORS에 대한 처리는 Backend Server에서 처리해야 한다. Client 측에서는 CORS 설정을 직접 할 수 없기 때문이다. 필자가 당면한 SpringBoot 환경에서의 CORS 문제를 어떻게 처리할 수 있을까?
  
## Spring Boot의 CORS
  
---
  
# 연결문서
