---
title : "DBCP"
excerpt : "DBCP"
toc : true
toc_sticky : true
toc_label : "DBCP"
categories:
- ServerCommon
tags:
- [ServerCommon, Database]
last_modified_at: 2024-03-16T08:00:00-10:00:00
---
  
---
  
> **DBCP 란?**  
>
> Database Connection Pool의 약어로 Database와 연결된 Connection 을 미리 만들어 Pool에 저장하고 관리하는 Connection 관리 방식이다. 
{: .notice--info}  

 DBCP의 WorkFlow를 살펴보자.

 먼저 **DB Connection 객체를 여러 개 생성 후 Pool에 보관**한다. 그리고 Connection이 **필요할 경우 Pool에서 Connection을 가져와 사용**한다. 만약 가용한 Connection이 Pool에 없다면 **Client 는 Connection이 생길 때까지 대기**한다. Connection **사용이 끝났다면, Connection을 Pool에 반환**한다.

> **memo**
>
> WAS가 Database에 접근할때마다 Connection을 생성한다면 비용이 낭비되는데, Connection Pool 방식을 사용하면 비용을 줄일 수 있다. 또한 커넥션 수를 제한할 수 있어 서버자원 고갈을 방지할 수 있다. 
{: .notice--info}  

---
  
# 연결문서
