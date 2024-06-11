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
  
## 정의
> **DBCP 란?**  
>
> Database Connection Pool
> Database와 연결된 Connection 을 미리 만들어 Pool에 저장하고 관리하는 Connection 관리 방식 
{: .notice--info}  
  
## DBCP Work Flow
- DB Connection 객체를 여러개 생성 후 Pool에 보관
- Connection이 필요할 경우 Pool에서 가져와 사용
- 가용 Connection이 Pool에 없다면 Client 는 가용 Connection이 생길때까지 대기
- 사용이 끝난 Connection은 Pool에 반환

> **memo**
>
> WAS가 Database에 접근할때마다 Connection을 생성한다면 비용이 낭비되는데, Connection Pool 방식을 사용하면 비용을 줄일 수 있다. 또한 커넥션 수를 제한할 수 있어 서버자원 고갈을 방지할 수 있다. 
{: .notice--info}  

---
  
# 연결문서
