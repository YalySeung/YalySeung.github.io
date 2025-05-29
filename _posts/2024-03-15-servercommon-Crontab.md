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
  
## 📌 Crontab이란?

> **info**
>
> Crontab은 Linux 운영체제에서 **정기적으로 명령어나 스크립트를 실행할 수 있도록 스케줄링하는 도구**이다.  
> 시스템 백업, 로그 정리, 데이터 수집 등 자동화 작업에 주로 사용된다. 
{: .notice--info}  

---
  
## ✅ 주요 명령어 정리

| 명령어 | 설명 |
|--------|------|
| `sudo apt install cron` | 크론 설치 (Debian 계열) |
| `sudo service cron status` | 크론 서비스 상태 확인 |
| `sudo service cron start` | 크론 서비스 시작 |
| `sudo service cron restart` | 크론 서비스 재시작 |
| `crontab -l` | 현재 사용자에 등록된 크론 작업 확인 |
| `crontab -e` | 크론 편집기 열기 (작업 등록) |

---
  
## ✅ Crontab 사용 전 준비

- 실행할 **Shell 파일에 실행 권한 부여** 필요
  
```bash
chmod 755 <shell 파일명>
```

---
  
## ✅ Crontab 스케줄 등록 형식
  
```bash
  
# crontab -e 편집기 내 입력 예시
  
# ┌──────── 분 (0 - 59)
  
# │ ┌────── 시 (0 - 23)
  
# │ │ ┌──── 일 (1 - 31)
  
# │ │ │ ┌── 월 (1 - 12)
  
# │ │ │ │ ┌─ 요일 (0 - 6) (일: 0 또는 7)
  
# │ │ │ │ │
  
# │ │ │ │ │
  
# * * * * * 명령어
```

---
  
## ✅ 예시: 매일 06:30에 스크립트 실행
  
```bash
30 06 * * * /Tomcat 홈 경로/logs/sampleLog.sh
```

> **tip**
>
> `crontab -e`는 현재 로그인된 사용자 기준으로 설정된다. 시스템 전체 작업은 `/etc/crontab` 또는 `/etc/cron.d/` 사용. 
{: .notice--info}  

---
  
## ✅ 로그 확인 방법
  
```bash
cat /var/log/syslog | grep CRON  # Debian 계열
cat /var/log/cron.log            # RHEL/CentOS 계열
```

---
  
## ✅ 주의 사항

- **환경 변수 설정 필요할 수 있음** (`PATH`, `JAVA_HOME` 등)
- **상대 경로보다는 절대 경로 사용 권장**
- 실행 로그 확인 및 리디렉션 (`>> ~/cron.log 2>&1`) 설정 권장

---
  
# 연결문서
- [CLI-BaseCommand](../../cli/cli-CLI-BaseCommand)
- [Linux-Command-Detail](../../cli/cli-Linux-Command-Detail)
- [Cron Expression](../../expression/expression-Cron-Expression)
- [Log Rolling](../../servercommon/servercommon-Log-Rolling)
