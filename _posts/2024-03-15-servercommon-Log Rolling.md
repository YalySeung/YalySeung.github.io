---
title : "Log Rolling"
excerpt : "Log Rolling"
toc : true
toc_sticky : true
toc_label : "Log Rolling"
categories:
- ServerCommon
tags:
- [ServerCommon]
last_modified_at: 2024-03-15T08:00:00-10:00:00
---
  
---
  
## 📌 Log Rolling이란?

> **info**
>
> Log Rolling은 로그 파일의 **크기 또는 시간**을 기준으로  
> **기존 로그 파일을 백업하고 새 로그 파일로 교체하는 프로세스**이다.  
> 로그 파일이 과도하게 커지는 것을 방지하고, **디스크 공간 관리 및 로그 분석을 용이하게 한다.** 
{: .notice--info}  

---
  
## ✅ Log Rolling의 역할

- 로그 파일 크기 제한을 통해 **디스크 사용 최적화**
- **오래된 로그를 자동 보관 또는 삭제**
- 운영 중인 시스템에서 **지속적인 로그 수집 가능**
- 시스템 장애 분석, 보안 감사 등의 **로그 분석 효율성 향상**

---
  
## ✅ Rolling 방식
  
### 🔹 1. 크기 기반 Rolling (Size-Based)

> 설정한 최대 크기를 초과하면 새 로그 파일 생성 
{: .notice}  

- 예: `app.log`가 10MB 초과 → `app.log.1`, `app.log.2` 등으로 백업
  
```properties
logging.file.max-size=10MB
logging.file.max-history=30
```

---
  
### 🔹 2. 시간 기반 Rolling (Time-Based)

> 일정 주기마다 새 로그 파일로 자동 전환 
{: .notice}  

- 일별/주별/월별 등 주기 설정 가능
- 예: 하루가 지나면 `app-2024-05-07.log` 등으로 저장
  
```xml
<rollingPolicy class="TimeBasedRollingPolicy">
    <fileNamePattern>logs/app-%d{yyyy-MM-dd}.log</fileNamePattern>
    <maxHistory>30</maxHistory>
</rollingPolicy>
```

---
  
### 🔹 3. 혼합 기반 Rolling (Size + Time Hybrid)

> 로그 크기와 시간 조건 중 **어느 하나라도 충족 시 롤링 수행** 
{: .notice}  

- 유연한 로그 관리 정책 가능
- Spring Boot, Logback 등에서 설정 가능

---
  
## ✅ Spring Boot + Logback 적용 예시
  
```xml
<appender name="ROLLING" class="ch.qos.logback.core.rolling.RollingFileAppender">
    <file>logs/app.log</file>
    <rollingPolicy class="ch.qos.logback.core.rolling.TimeBasedRollingPolicy">
        <fileNamePattern>logs/app-%d{yyyy-MM-dd}.%i.log</fileNamePattern>
        <maxHistory>7</maxHistory>
        <timeBasedFileNamingAndTriggeringPolicy class="ch.qos.logback.core.rolling.SizeAndTimeBasedFNATP">
            <maxFileSize>10MB</maxFileSize>
        </timeBasedFileNamingAndTriggeringPolicy>
    </rollingPolicy>
    <encoder>
        <pattern>%d %-5level %logger{36} - %msg%n</pattern>
    </encoder>
</appender>
```

---
  
## ✅ 관련 도구 및 기술

| 도구 | 설명 |
|------|------|
| **Logback** | Spring Boot 기본 로깅 프레임워크 |
| **Log4j2** | 고성능 로깅, 다양한 설정 지원 |
| **Crontab** | 수동 로그 삭제 및 스케줄링 가능 |
| **logrotate(Linux)** | 시스템 로그 자동 롤링 및 압축 도구 |

---
  
# 연결문서
- [Crontab](../../servercommon/servercommon-Crontab)
- [log4j](../../servercommon/servercommon-log4j)
