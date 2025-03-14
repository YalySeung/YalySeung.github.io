---
title : "Tomcat logging"
excerpt : "Tomcat logging"
toc : true
toc_sticky : true
toc_label : "Tomcat logging"
categories:
- ServerCommon
tags:
- [ServerCommon]
last_modified_at: 2024-03-15T08:00:00-10:00:00
---
  
---
  
  이 글에서는 Tomcat 에서 Logging하는 방법을 알아보겠다.
  
  Tomcat 설치 후 별도의 설정을 하지 않았다면 기본 로그 경로는 `Tomcat/logs` 폴더이다.
  
## 경로 설정
  Tomcat의 로그 설정은 `Tomcat/conf/server.xml`에서 관리된다.  
  `Valve`의 `directory` 속성이 로그의 root 폴더 경로를 지정한다.
  
```xml
<Valve className="org.apache.catalina.valves.AccessLogValve" directory="logs"
       prefix="localhost_access_log" suffix=".txt"
       pattern="%h %l %u %t &quot;%r&quot; %s %b" />
```
  
## Catalina.out
- **서버에서 발생한 모든 내용(기동, 정지 등)을 기록**  
- 기본 설정은 하나의 파일에 로그가 계속 쌓이며, 날짜별로 분리하려면 [Crontab](../../servercommon/servercommon-Crontab)을 사용해야 한다.
  
### 경로 설정
- `Tomcat/bin/Catalina.out`
  
```bash
if [ -z "$CATALINA_OUT" ] ; then
  # 경로 설정
  CATALINA_OUT="$CATALINA_BASE"/logs/catalina.out
  # 로깅 비활성화 설정
  CATALINA_OUT=/dev/null
fi
```
  
### Crontab을 활용한 로그 분리
  
```bash
  
# Catalina.out 로그 날짜별로 분리
cp /Tomcat 홈 경로/logs/catalina.out /Tomcat 홈 경로/logs/catalina.out.$(date +\%y-\%m-\%d).log 2>&1
  
# 기존 catalina.out 로그 내용 제거
cat /dev/null > /Tomcat 홈 경로/logs/catalina.out
  
# 90일이 지난 파일 삭제
find /Tomcat 홈 경로/logs -mtime +90 -name catalina* -exec rm {} \;
```
  
## 기타 로그 파일
  
### catalina.yyyy-mm-dd.log
- **Tomcat 내부 로깅을 기록**  
- Standard output, Standard error 로그 제외
  
### host-manager.log
- **Tomcat Host Manager Web App 관련 로그**
  
### manager.log
- **Tomcat Manager Web App 관련 로그**
  
### localhost.log
- **개별 호스트의 로그 기록**
  
## 로그 설정 변경
  위 파일들의 경로 및 로깅 수준은 `Tomcat/conf/logging.properties`에서 설정 가능하다.
  
```bash
  
# catalina.yyyy-mm-dd.log 설정
1catalina.org.apache.juli.AsyncFileHandler.level = FINE
1catalina.org.apache.juli.AsyncFileHandler.directory = ${catalina.base}/logs
1catalina.org.apache.juli.AsyncFileHandler.prefix = catalina.
1catalina.org.apache.juli.AsyncFileHandler.encoding = UTF-8
  
# localhost.log 설정
2localhost.org.apache.juli.AsyncFileHandler.level = FINE
2localhost.org.apache.juli.AsyncFileHandler.directory = ${catalina.base}/logs
2localhost.org.apache.juli.AsyncFileHandler.prefix = localhost.
2localhost.org.apache.juli.AsyncFileHandler.encoding = UTF-8
```

---
  
# 연결문서
- [Tomcat](../../servercommon/servercommon-Tomcat)
- [Tomcat 설정](../../servercommon/servercommon-Tomcat-설정)
- [Crontab](../../servercommon/servercommon-Crontab)
