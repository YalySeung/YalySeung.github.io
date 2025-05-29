---
title : "Daemon Process"
excerpt : "Daemon Process"
toc : true
toc_sticky : true
toc_label : "Daemon Process"
categories:
- ServerCommon
tags:
- [ServerCommon]
last_modified_at: 2023-10-15T08:00:00-10:00:00
---
  
---
  
## 📌 Daemon Process란?

> **info**
>
> Daemon Process는 리눅스/유닉스 운영체제에서 **사용자 개입 없이 백그라운드에서 지속적으로 동작하는 프로세스**를 의미한다.  
> 시스템 부팅 시 자동으로 실행되며, 클라이언트의 요청에 응답하거나 특정 작업을 주기적으로 수행한다. 
{: .notice--info}  

---
  
## ✅ Daemon 프로세스의 특징

- 백그라운드 실행 (`&` 기호 또는 systemd, init 등으로 시작)
- 부모 프로세스가 `init(1)` 또는 `systemd(1)`
- 로그인 세션에 의존하지 않음
- 이름이 `d`로 끝나는 경우가 많음 (ex. `sshd`, `httpd`, `crond`)

---
  
## ✅ 대표적인 Daemon 프로세스 예시

| 이름 | 설명 |
|------|------|
| `sshd` | SSH 접속을 관리 |
| `httpd` | Apache HTTP 서버 |
| `crond` | crontab 기반 스케줄링 |
| `systemd` | 시스템 부팅 및 서비스 관리 |
| `mysqld` | MySQL DB 서비스 프로세스 |

---
  
## ✅ Daemon 프로세스 확인 방법
  
```bash
ps -ef | grep 'd$'
```

또는 systemd 기반 서비스 확인:
  
```bash
systemctl list-units --type=service
```

---
  
## ✅ Daemon 작성 (C 예시)
  
```c
  
#include <stdio.h>
  
#include <stdlib.h>
  
#include <unistd.h>
  
#include <sys/types.h>

int main() {
    pid_t pid = fork();

    if (pid < 0) exit(EXIT_FAILURE);
    if (pid > 0) exit(EXIT_SUCCESS); // Parent 종료

    // 자식 프로세스는 세션 리더가 되고 터미널 분리
    setsid();

    while (1) {
        // 백그라운드 작업 수행
        sleep(30);
    }

    return 0;
}
```

---
  
## ✅ 관련 개념

- **Foreground Process**: 사용자와 직접 상호작용하는 터미널 기반 프로세스
- **Background Process**: 터미널에서 `&`로 실행되며, 사용자와 직접적 인터랙션 없음
- **Service Manager**: systemd, init.d, launchd 등 데몬의 실행과 상태를 제어

---
  
# 연결문서
- [Crontab](../../servercommon/servercommon-Crontab)
- [Linux-Systemd](../../os/os-Linux-Systemd)
