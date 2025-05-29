---
title : "Linux Systemd"
excerpt : "Linux Systemd"
toc : true
toc_sticky : true
toc_label : "Linux Systemd"
categories:
- OS
tags:
- [Linux]
last_modified_at: 2025-05-07T08:00:00-10:00:00
---
  
---
  
## 📌 systemd란?

> **info**
>
> systemd는 리눅스 운영체제에서 **시스템 및 서비스의 부팅, 관리, 추적을 담당하는 초기화(init) 시스템**이다.  
> `init.d`, `upstart`를 대체하며, 현대적인 **병렬 처리 기반의 서비스 관리 기능**을 제공한다. 
{: .notice--info}  

---
  
## ✅ systemd의 주요 기능

- **서비스 단위(Unit)**로 프로세스/타이머/소켓 등 관리
- **병렬 부팅 처리로 빠른 시작 시간 보장**
- **의존성 기반 실행 순서 제어**
- **로깅(Journal) 내장**
- **타이머 기반 예약 작업(systemd-timer)**

---
  
## ✅ 주요 Unit 종류

| 단위(Unit) | 설명 |
|------------|------|
| service    | 데몬, 백그라운드 서비스 |
| socket     | 소켓 기반 활성화 |
| target     | 실행 그룹 묶음 (ex: multi-user.target) |
| mount      | 파일 시스템 마운트 |
| timer      | crontab 대체 가능 예약 실행 |

---
  
## ✅ systemctl 명령어

| 명령어 | 설명 |
|--------|------|
| `systemctl start nginx` | nginx 서비스 시작 |
| `systemctl stop nginx` | nginx 서비스 중단 |
| `systemctl restart nginx` | nginx 서비스 재시작 |
| `systemctl status nginx` | nginx 상태 확인 |
| `systemctl enable nginx` | 부팅 시 자동 시작 등록 |
| `systemctl disable nginx` | 자동 시작 해제 |

---
  
## ✅ 서비스 등록 예시

1. 서비스 유닛 파일 생성: `/etc/systemd/system/myapp.service`
  
```ini
[Unit]
Description=My Custom App Service
After=network.target

[Service]
ExecStart=/usr/bin/java -jar /opt/myapp/myapp.jar
Restart=always
User=nobody

[Install]
WantedBy=multi-user.target
```

2. 적용 및 실행
  
```bash
sudo systemctl daemon-reexec     # 또는 daemon-reload
sudo systemctl enable myapp
sudo systemctl start myapp
```

---
  
## ✅ 로그 확인 (journalctl)
  
```bash
journalctl -u myapp.service        # 특정 서비스 로그 확인
journalctl -xe                     # 최근 에러 로그
journalctl --since "10 minutes ago"
```

---
  
## ✅ systemd vs init 비교

| 항목 | systemd | SysV init |
|------|---------|------------|
| 병렬 실행 | O | X |
| 의존성 관리 | O | X |
| 유닛 단위 관리 | O | X |
| 로그 시스템 | journalctl | /var/log/messages |
| 서비스 제어 | systemctl | service |

---
  
# 연결문서
- [Daemon Process](../../servercommon/servercommon-Daemon-Process)
- [Crontab](../../servercommon/servercommon-Crontab)
