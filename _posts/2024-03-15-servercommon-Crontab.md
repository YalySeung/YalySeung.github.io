---
title : "Crontab"
excerpt : "Crontab"
toc : true
toc_sticky : true
toc_label : "Crontab"
categories:
- ServerCommon
tags:
- [ServerCommon, Linux]
last_modified_at: 2024-03-15T08:00:00-10:00:00
---
  
---
  
> **Crontab이란**  
>
> Linux 운영체제에서 배치 작업을 스케쥴링 하기 위한 프로그램이다. 
{: .notice--info}  
  
## 명령어
 Linux에서 사용하는 Crontab 명령어를 알아보자.

| Linux 명령어                 | 기능            |
| ------------------------- | ------------- |
| sudo apt install cron     | 설치            |
| sudo service cron status  | 상태 조회         |
| sudo service cron start   | 서비스 시작        |
| sudo service cron restart | 재시작           |
| crontab -l                | 할당된 작업 리스트 조회 |
| crontab -e                | 스크립트 작성       |

 Crontab을 사용하여 스케쥴을 등록해보자. 먼저 스케쥴로 실행할 **파일에 실행 권한을 부여**해야한다.
  
```bash
chmod 755 <shell 파일명> 
{: .notice}  
```

 파일 실행 권한을 부여했다면, **crontab <크론식> 파일경로** 형식으로 스케쥴을 등록한다. 아래 예시는 **매일 6시 30분마다 shell 파일을 실행**하는 예시이다. 
{: .notice}  
  
```bash
  
# 매일 06:30분에 sampleLog.sh 파일 실행
$ crontab -e
30 06 * * * /Tomcat 홈 경로/logs/sampleLog.sh
```

---
  
# 연결문서
- [CLI-BaseCommand](../../cli/cli-CLI-BaseCommand)
- [Linux-Command-Detail](../../cli/cli-Linux-Command-Detail)
- [Cron Expression](../../expression/expression-Cron-Expression)
- [Log Rolling](../../servercommon/servercommon-Log-Rolling)