---
title : "Tomcat logging"
excerpt : "Tomcat logging"
toc : true
toc_sticky : true
toc_label : "Tomcat logging"
categories:
- ServerCommon
tags:
- [ServerCommon, 미완료]
last_modified_at: 2024-03-15T08:00:00-10:00:00
---

# 날짜 : 2024-03-15 13:35

# 태그 : #ServerCommon #미완료 
---

# 내용

## 로그 root
- 기본으로 Tomcat 폴더 내의 logs 폴더를 사용

### 경로설정
- Tomcat/conf/server.xml
- Valve의 directory 가 로그 root 폴더 경로를 의미한다.

```bash
...
<Valve className="org.apache.catalina.valves.AccessLogValve" directory="logs"
               prefix="localhost_access_log" suffix=".txt"
               pattern="%h %l %u %t &quot;%r&quot; %s %b" />
...
```

## Catalina.out
- 서버에서 발생한 모든 내용(기동, 정지 등)을 기록한 파일
- 기본설정은 한 파일에 모든 로그가 쌓이도록 설정되어있어, 날짜별로 분리하러면 [Crontab](../../servercommon/servercommon-Crontab)을 사용해야한다.

### 경로 설정
- Tomcat/bin/Catalina.out

```bash
...
if [ -z "$CATALINA_OUT" ] ; then
  #경로설정
  CATALINA_OUT="$CATALINA_BASE"/logs/catalina.out
  #로깅 안할경우
  CATALINA_OUT=/dev/null
fi
...
```

### Crontab 스크립트 작성

```bash

# Catalina.out 로그 날짜별로 분리
cp /Tomcat 홈 경로/logs/catalina.out /Tomcat 홈 경로/logs/catalina.out.$(date +\%y-\%m-\%d).log 2>&1

# 기존의 catalina.out 로그 내용 제거
cat /dev/null > /Tomcat 홈 경로/logs/catalina.out

# 생성 후 90일이 지난 파일 삭제
find /Tomcat 홈 경로/logs -mtime +90 -name catalina* -exec rm {} \;
```

## catalina.yyyy-mm-dd.log
- 톰캣에서 생기는 로그만 기록
- Standard output, Standard error 로그는 제외

## host-manager.log
- Tomcat Host Manager Web app 로그

## manager.log
- Tomcat Manager Web App 로그

## localhost.log
- host 한정 로그

### [catalina.yyyy-mm-dd.log](#catalinayyyy-mm-ddlog), [host-manager.log](#host-managerlog), [manager.log](#managerlog), [localhost.log](#localhostlog) 경로 설정
- 모두  Tomcat/api/conf/logging.properties 파일에서 설정 가능하다

```bash
...

# catalina.yyyy-mm-dd.log
1catalina.org.apache.juli.AsyncFileHandler.level = FINE
1catalina.org.apache.juli.AsyncFileHandler.directory = ${catalina.base}/logs
1catalina.org.apache.juli.AsyncFileHandler.prefix = catalina.
1catalina.org.apache.juli.AsyncFileHandler.encoding = UTF-8

# localhost.log
2localhost.org.apache.juli.AsyncFileHandler.level = FINE
2localhost.org.apache.juli.AsyncFileHandler.directory = ${catalina.base}/logs
2localhost.org.apache.juli.AsyncFileHandler.prefix = localhost.
2localhost.org.apache.juli.AsyncFileHandler.encoding = UTF-8

# manager.log
3manager.org.apache.juli.AsyncFileHandler.level = FINE
3manager.org.apache.juli.AsyncFileHandler.directory = ${catalina.base}/logs
3manager.org.apache.juli.AsyncFileHandler.prefix = manager.
3manager.org.apache.juli.AsyncFileHandler.encoding = UTF-8

# host-manager.log
4host-manager.org.apache.juli.AsyncFileHandler.level = FINE
4host-manager.org.apache.juli.AsyncFileHandler.directory = ${catalina.base}/logs
4host-manager.org.apache.juli.AsyncFileHandler.prefix = host-manager.
4host-manager.org.apache.juli.AsyncFileHandler.encoding = UTF-8
...
```

---

# 연결문서
- [Tomcat](../../servercommon/servercommon-Tomcat)
- [Tomcat 설정](../../servercommon/servercommon-Tomcat-설정)
- [Crontab](../../servercommon/servercommon-Crontab)