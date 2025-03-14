---
title : "log4j"
excerpt : "log4j"
toc : true
toc_sticky : true
toc_label : "log4j"
categories:
- ServerCommon
tags:
- [ServerCommon]
last_modified_at: 2024-05-14T08:00:00-10:00:00
---
  
---
  
> **log4j 설정 파일 `logback.xml`**  
>
>  Logback 설정 파일을 활용하여 로그 파일을 관리하는 방법을 정리한다. 
{: .notice--info}  

  Logback을 활용하면 **로그 파일을 자동으로 분류하고, 크기 및 날짜 기준으로 롤링할 수 있다.**  
  
## logback.xml 설정 예제
  
```xml
<?xml version="1.0" encoding="UTF-8"?>  
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
        <encoder>  
            <pattern>[%d] [%thread] %-5level %logger{36}.%M:%L - %msg%n</pattern>  
        </encoder>  
    </appender>  

    <appender name="viewErrorLogAppender" class="ch.qos.logback.core.rolling.RollingFileAppender">  
        <file>${LOG_HOME}/view/error/viewError.log</file>  
        <rollingPolicy class="ch.qos.logback.core.rolling.SizeAndTimeBasedRollingPolicy">  
            <fileNamePattern>${LOG_HOME}/view/error/viewError.%d{yyyy-MM-dd}.%i.log</fileNamePattern>  
            <maxFileSize>30MB</maxFileSize>  
            <maxHistory>30</maxHistory>  
        </rollingPolicy>  
        <encoder>  
            <pattern>[%d] [%thread] %-5level %logger{36}.%M:%L - %msg%n</pattern>  
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
  
## property 요소 설정
  
```xml
<property scope="context" name="LOG_HOME" value="/home/rpa" />
```

  XML에서 사용할 **변수를 선언**하는 부분이다. `scope` 값은 아래와 같이 설정할 수 있다.

| scope 값 | 기능 |
| ------- | -------------------------------------- |
| local   | 특정 `<bean>` 요소 내에서만 적용 |
| global  | 전역 설정으로 모든 bean에 영향 |
| context | 애플리케이션 전체에서 사용 가능 |
  
## 장점과 단점
  
### ✅ 장점
- **로그를 파일 크기 및 날짜 기준으로 롤링 가능**  
- **로그 레벨을 설정하여 필요 없는 로그 필터링 가능**  
- **다양한 출력 형태(Console, File 등) 지원**  
  
### ❌ 단점
- **설정이 많아 초기 구성 시간이 걸릴 수 있음**  
- **YAML 설정 방식과 혼합 사용 시 충돌 가능**  

---
  
# 연결문서
