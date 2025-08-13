---
title : "Linux Directories"
excerpt : "Linux Directories"
toc : true
toc_sticky : true
toc_label : "Linux Directories"
categories:
- OS
tags:
- [Linux, OS]
last_modified_at: 2025-06-09T08:00:00-10:00:00
---
  
---
  
## 📌 리눅스 주요 디렉토리 구조 설명

> **info**
>
> 리눅스는 **계층적 디렉토리 구조**를 가지며, 모든 파일과 디렉토리는 루트(`/`)에서 시작된다.  
> 각각의 디렉토리는 **특정한 시스템 역할과 목적**을 가지고 있다. 
{: .notice--info}  

---
  
## ✅ 주요 디렉토리 목록

| 디렉토리 | 설명 |
|----------|------|
| `/` | 루트 디렉토리, 최상위 디렉토리 |
| `/bin` | 사용자 명령어 실행파일 (ls, cp 등 기본 명령어) |
| `/boot` | 부트로더, 커널 등 부팅 관련 파일 |
| `/dev` | 하드웨어 장치 파일 (예: `/dev/sda`, `/dev/null`) |
| `/etc` | 시스템 설정 파일 (config, init.d 등) |
| `/home` | 일반 사용자 디렉토리 (예: `/home/얄리`) |
| `/lib` | 시스템 실행에 필요한 라이브러리 |
| `/media` | 외부 장치 자동 마운트 위치 (USB 등) |
| `/mnt` | 임시 마운트 지점 |
| `/opt` | 추가 응용프로그램 설치 위치 |
| `/proc` | 프로세스 및 커널 정보 (가상 파일 시스템) |
| `/root` | 관리자(root)의 홈 디렉토리 |
| `/run` | 부팅 중 생성되는 임시 파일 |
| `/sbin` | 시스템 관리 명령어 (shutdown, mount 등) |
| `/srv` | 서비스 관련 데이터 저장 위치 (웹, FTP 등) |
| `/sys` | 시스템 및 커널 관련 정보 제공 (가상 파일 시스템) |
| `/tmp` | 임시 파일 저장소 (자동 삭제됨) |
| `/usr` | 사용자 애플리케이션 및 라이브러리 |
| `/var` | 가변 데이터 (로그, 큐, 스풀, DB 등) |

---
  
## ✅ `/usr` 하위 구조

| 디렉토리 | 설명 |
|----------|------|
| `/usr/bin` | 일반 사용자용 실행 파일 |
| `/usr/sbin` | 관리자용 실행 파일 |
| `/usr/lib` | 프로그램 실행에 필요한 라이브러리 |
| `/usr/local` | 사용자 정의 로컬 프로그램 설치 위치 |

---
  
## ✅ `/var` 하위 구조

| 디렉토리 | 설명 |
|----------|------|
| `/var/log` | 시스템 로그 파일 |
| `/var/spool` | 메일, 프린터 대기열 등 |
| `/var/tmp` | 장기 임시파일 |
| `/var/www` | 웹 서비스 콘텐츠 디렉토리 |

---
  
# 연결문서
- [Linux-Command-Detail](../../cli/cli-Linux-Command-Detail)
- [Crontab](../../servercommon/servercommon-Crontab)