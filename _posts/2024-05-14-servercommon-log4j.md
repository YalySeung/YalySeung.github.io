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
<configuration>  
    <property scope="context" name="LOG_HOME" value="/home/rpa" />  
  
    <appender name="console" class="ch.qos.logback.core.ConsoleAppender">  
        <encoder class="ch.qos.logback.classic.encoder.PatternLayoutEncoder">  
            <pattern>[%d] [%thread] %-5level %logger{36}.%M:%L - %msg%n</pattern>  
        </encoder>  
    </appender>  
      <appender name="viewLogAppender" class="ch.qos.logback.core.rolling.RollingFileAppender">  
        <file>${LOG_HOME}/view/view.log</file>  
        <rollingPolicy class="ch.qos.logback.core.rolling.SizeAndTimeBasedRollingPolicy">  
            <fileNamePattern>${LOG_HOME}/view/view.%d{yyyy-MM-dd}.%i.log</fileNamePattern>  
            <maxFileSize>30MB</maxFileSize>  
            <maxHistory>30</maxHistory>  
        </rollingPolicy>  
        <encoder>            <pattern>[%d] [%thread] %-5level %logger{36}.%M:%L - %msg%n</pattern>  
        </encoder>  
    </appender>  
    <appender name="viewErrorLogAppender" class="ch.qos.logback.core.rolling.RollingFileAppender">  
        <file>${LOG_HOME}/view/error/viewError.log</file>  
        <rollingPolicy class="ch.qos.logback.core.rolling.SizeAndTimeBasedRollingPolicy">  
            <fileNamePattern>${LOG_HOME}/view/error/viewError.%d{yyyy-MM-dd}.%i.log</fileNamePattern>  
            <maxFileSize>30MB</maxFileSize>  
            <maxHistory>30</maxHistory>  
        </rollingPolicy>  
        <encoder>            <pattern>[%d] [%thread] %-5level %logger{36}.%M:%L - %msg%n</pattern>  
        </encoder>  
        <filter class="ch.qos.logback.classic.filter.LevelFilter">  
            <level>ERROR</level>  
            <onMatch>ACCEPT</onMatch>  
            <onMismatch>DENY</onMismatch>  
        </filter>  
    </appender>  
  
    <logger name="org.sample.api.data.mapper" additivity="false">  
        <level value="DEBUG"/>  
        <appender-ref ref="console"/>  
    </logger>  
    <logger name="org.sample.view.data.mapper" additivity="false">  
        <level value="DEBUG"/>  
        <appender-ref ref="viewLogAppender"/>  
    </logger>  
  
    <logger name="org.hibernate" additivity="false">  
        <level value="TRACE"/>  
        <appender-ref ref="viewLogAppender"/>  
        <appender-ref ref="console" />  
    </logger>  
  
    <root level="DEBUG">  
        <appender-ref ref="console" />  
        <appender-ref ref="viewLogAppender" />  
        <appender-ref ref="viewErrorLogAppender" />  
    </root>  
        </configuration>
  
``` 
  
## property 요소
  
```java
<property scope="context" name="LOG_HOME" value="/home/rpa" />
```
 XML에서 사용할 **변수를 선언**하는 부분이라고 보면 된다. 속성중 scope는 아래의 세가지 옵션으로 설정이 가능하다. 
 
| scope 값 | 기능                                                |
| ------- | ------------------------------------------------- |
| local   | \<bean\> 요소의 로컬 설정으로 간주된다. 현재 bean의 요소에만 영향을 미친다. |
| global  | 전역 설정으로 간주되어 모든 bean에 영향을 미친다.                    |
| context | 해당 애플리케이션 컨텍스트의 범위로 간주되어 애플리케이션 전체에 영향을 미친다.      |

---
  
# 연결문서
