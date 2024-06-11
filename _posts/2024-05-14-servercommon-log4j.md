---
title : "log4j"
excerpt : "log4j"
toc : true
toc_sticky : true
toc_label : "log4j"
categories:
- ServerCommon
tags:
- [ServerCommon, 미완료]
last_modified_at: 2024-05-14T08:00:00-10:00:00
---
  
---
  
 log4j 설정파일 **logback.xml** 에 대해서 알아보자. 
  
```java
3<?xml version="1.0" encoding="UTF-8"?>   
{: .notice}  
<configuration>   
{: .notice}  
    <property scope="context" name="LOG_HOME" value="/home/rpa" />   
{: .notice}  
  
    <appender name="console" class="ch.qos.logback.core.ConsoleAppender">   
{: .notice}  
        <encoder class="ch.qos.logback.classic.encoder.PatternLayoutEncoder">   
{: .notice}  
            <pattern>[%d] [%thread] %-5level %logger{36}.%M:%L - %msg%n</pattern>   
{: .notice}  
        </encoder>   
{: .notice}  
    </appender>   
{: .notice}  
      <appender name="viewLogAppender" class="ch.qos.logback.core.rolling.RollingFileAppender">   
{: .notice}  
        <file>${LOG_HOME}/view/view.log</file>   
{: .notice}  
        <rollingPolicy class="ch.qos.logback.core.rolling.SizeAndTimeBasedRollingPolicy">   
{: .notice}  
            <fileNamePattern>${LOG_HOME}/view/view.%d{yyyy-MM-dd}.%i.log</fileNamePattern>   
{: .notice}  
            <maxFileSize>30MB</maxFileSize>   
{: .notice}  
            <maxHistory>30</maxHistory>   
{: .notice}  
        </rollingPolicy>   
{: .notice}  
        <encoder>            <pattern>[%d] [%thread] %-5level %logger{36}.%M:%L - %msg%n</pattern>   
{: .notice}  
        </encoder>   
{: .notice}  
    </appender>   
{: .notice}  
    <appender name="viewErrorLogAppender" class="ch.qos.logback.core.rolling.RollingFileAppender">   
{: .notice}  
        <file>${LOG_HOME}/view/error/viewError.log</file>   
{: .notice}  
        <rollingPolicy class="ch.qos.logback.core.rolling.SizeAndTimeBasedRollingPolicy">   
{: .notice}  
            <fileNamePattern>${LOG_HOME}/view/error/viewError.%d{yyyy-MM-dd}.%i.log</fileNamePattern>   
{: .notice}  
            <maxFileSize>30MB</maxFileSize>   
{: .notice}  
            <maxHistory>30</maxHistory>   
{: .notice}  
        </rollingPolicy>   
{: .notice}  
        <encoder>            <pattern>[%d] [%thread] %-5level %logger{36}.%M:%L - %msg%n</pattern>   
{: .notice}  
        </encoder>   
{: .notice}  
        <filter class="ch.qos.logback.classic.filter.LevelFilter">   
{: .notice}  
            <level>ERROR</level>   
{: .notice}  
            <onMatch>ACCEPT</onMatch>   
{: .notice}  
            <onMismatch>DENY</onMismatch>   
{: .notice}  
        </filter>   
{: .notice}  
    </appender>   
{: .notice}  
  
    <logger name="org.sample.api.data.mapper" additivity="false">   
{: .notice}  
        <level value="DEBUG"/>   
{: .notice}  
        <appender-ref ref="console"/>   
{: .notice}  
    </logger>   
{: .notice}  
    <logger name="org.sample.view.data.mapper" additivity="false">   
{: .notice}  
        <level value="DEBUG"/>   
{: .notice}  
        <appender-ref ref="viewLogAppender"/>   
{: .notice}  
    </logger>   
{: .notice}  
  
    <logger name="org.hibernate" additivity="false">   
{: .notice}  
        <level value="TRACE"/>   
{: .notice}  
        <appender-ref ref="viewLogAppender"/>   
{: .notice}  
        <appender-ref ref="console" />   
{: .notice}  
    </logger>   
{: .notice}  
  
    <root level="DEBUG">   
{: .notice}  
        <appender-ref ref="console" />   
{: .notice}  
        <appender-ref ref="viewLogAppender" />   
{: .notice}  
        <appender-ref ref="viewErrorLogAppender" />   
{: .notice}  
    </root>   
{: .notice}  
        </configuration> 
{: .notice}  
  
``` 
  
## property 요소
  
```java
<property scope="context" name="LOG_HOME" value="/home/rpa" /> 
{: .notice}  
```
 XML에서 사용할 **변수를 선언**하는 부분이라고 보면 된다. 속성중 scope는 아래의 세가지 옵션으로 설정이 가능하다. 
 
| scope 값 | 기능                                                |
| ------- | ------------------------------------------------- |
| local   | \<bean\> 요소의 로컬 설정으로 간주된다. 현재 bean의 요소에만 영향을 미친다. | 
{: .notice}  
| global  | 전역 설정으로 간주되어 모든 bean에 영향을 미친다.                    |
| context | 해당 애플리케이션 컨텍스트의 범위로 간주되어 애플리케이션 전체에 영향을 미친다.      |

---
  
# 연결문서
