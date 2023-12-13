---
title : "Port"
excerpt : "Port"
toc : true
toc_sticky : true
toc_label : "Port"
categories:
- DevelopCommon
tags:
- [DevelopCommon]
last_modified_at: 2023-11-22T08:00:00-10:00:00
---

# 날짜 : 2023-11-22 12:28

# 태그 : #DevelopCommon
---

# 내용

## 정의
> Port 란
>컴퓨터 내에서 네트워크 서비스나 특정 프로세스를 식별하는 논리 단위

```
000.000.000.000:21
```

- 여기서 **:**의 앞부분은 **IP 주소**, 뒷부분은 **포트의 번호**

## Well-Known PORT 정보
- 0~1023 : Well-Known port
- 1024~49151 : register port
- 49152~65535 : dynamic port

### 자주 사용되는 포트

| 포트번호 | 프로토콜 | 용도                                                  |
| -------- | -------- | ----------------------------------------------------- |
| 20       | FTP      | FTP - 데이터 전송 포트                                |
| 21       | FTP      | FTP - 제어 포트                                       |
| 22       | SSH      | Secure Shell - ssh, sftp 같은 프로토콜 및 포트 포워딩 |
| 23       | Telnet   | 텔넷 프로토콜 - 암호화 되지 않는 텍스트 통신          |
| 25       | SMTP     | Simple Mail Transfer Protocol                         |
| 53       | DNS      | Domain Name System                                    |
| 80       | HTTP     | HyperText Transfer Protocol - 웹 페이지 전송 프로토콜 |
| 123      | NTP      | Network Time Protocol - 시간 동기화 프로토콜          |
| 443      | HTTPS    | HyperText Transfer Protocol over Secure Socket        |
| 514      | Syslog   | 시스템 로그 전송 프로토콜                             |

---

# 연결문서
- [DNS](../../servercommon/ServerCommon-DNS)
- [SSH](../../통신/통신-SSH)