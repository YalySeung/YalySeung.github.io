---
title : "shell"
excerpt : "shell"
toc : true
toc_sticky : true
toc_label : "shell"
categories:
- DevelopCommon
tags:
- [DevelopCommon]
last_modified_at: 2023-11-10T08:00:00-10:00:00
---

# 날짜 : 2023-11-10 14:26

# 태그 : #DevelopCommon 
---

# 내용

## shell 이란
- 커널과 사용자를 연결해주는 인터페이스
- 사용자가 입력하는 명령을 읽어 해석하고 프로그램을 실행시키는 인터페이스

## 기능
- 명령어 해석
- 쉘 자체 프로그래밍 기능
- 사용자 환경설정 기능

## 종류

### sh
- bourne shell
- 최초의 shell
- 대부분의 리눅스에 기본 설치
- /bin/sh

#### 기능
- 스크립트 지원

### ksh
- korn shell
- 유닉스에서 가장 많이 사용되는 [bourne shell](#sh)의 확장
- /bin/ksh

#### 기능
- 명령어 완성 기능, 히스토리 기능 지원

### bash
- bourne again shell
- Linux 표준 shell, [bourne shell](#sh)의 확장
- Linux, MAC OS X 등 다양한 OX에서 사용
- /bin/bash

#### 기능
- 명령어 완성기능
- 히스토리
- 명령어 치환, 편집
- POSIX와 호환 가능

### zsh
- z shell
- [bourne shell](#sh)의 확장, [korn shell](#ksh)의 재작성 shell
- /bin/zsh

#### 기능
- 강력한 히스토리 기능
- 향상된 명령행 편집 기능

### csh
- [bourne shell](#sh)의 사용성을 높인 shell
- /bin/csh

#### 기능
- C언어의 특징을 많이 포함
- 히스토리
- 별명
- 작업 제어

### tcsh
- tc shell, tee-see-shell
- [csh](#csh)의 기능을 강화한 shell
- BSD 계열에서 가장 많이 사용
- /bin/tcsh

#### 기능
- 명령어 편집 기능 제공

## 사용중인 shell 확인

```bash
echo $SHELL
```

![image](../../assets/Images/EchoShellResult.png)

---

# 연결문서
- [Linux-Command-Detail](../../CLI/CLI-Linux-Command-Detail)
- [Window-Command-Detail](../../CLI/CLI-Window-Command-Detail)