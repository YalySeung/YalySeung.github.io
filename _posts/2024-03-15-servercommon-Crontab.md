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
  
## 정의
> **Crontab이란**  
>
> Linux 운영체제에서 배치 작업을 스케쥴링 하기 위한 프로그램 
{: .notice--info}  
  
## 명령어

| Linux 명령어                 | 기능            |
| ------------------------- | ------------- |
| sudo apt install cron     | 설치            |
| sudo service cron status  | 상태 조회         |
| sudo service cron start   | 서비스 시작        |
| sudo service cron restart | 재시작           |
| crontab -l                | 할당된 작업 리스트 조회 |
| crontab -e                | 스크립트 작성       |
  
## 예시
  
### 실행파일 권한부여
  
```bash
chmod 755 <shell 파일명> 
{: .notice}  
```
  
### Crontab 등록
- <크론식> 파일경로 형식으로 등록한다. 
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