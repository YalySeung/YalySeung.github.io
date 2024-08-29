---
title : "Hibernate Logging"
excerpt : "Hibernate Logging"
toc : true
toc_sticky : true
toc_label : "Hibernate Logging"
categories:
- JPA
tags:
- [Spring, JPA]
last_modified_at: 2024-04-04T08:00:00-10:00:00
---
  
---
  
## logback 설정
  
```java
<?xml version="1.0" encoding="UTF-8"?>  
<configuration>
	...
	<logger name="org.hibernate" additivity="false">  
	    <level value="TRACE"/>  
	    <appender-ref ref="viewLogAppender"/>  
	    <appender-ref ref="console" />  
	</logger>
	...
</configuration>
```

> **tip**
>
> level을 TRACE로 설정해야 Query Param 값까지 확인 가능하다 
{: .notice--primary}  

---
  
# 연결문서
- [Hibernate](../../jpa/jpa-Hibernate)