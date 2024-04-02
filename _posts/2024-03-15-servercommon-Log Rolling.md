---
title : "Log Rolling"
excerpt : "Log Rolling"
toc : true
toc_sticky : true
toc_label : "Log Rolling"
categories:
- ServerCommon
tags:
- [ServerCommon]
last_modified_at: 2024-03-15T08:00:00-10:00:00
---

# 날짜 : 2024-03-15 14:21

# 태그 : #ServerCommon
---

# 내용

## 정의
> **Log Rolling 이란?**
>
> 로그 파일의 크기나 시간에 따라 기존 로그 파일을 벡업하고 새로운 로그파일을 생성하는 프로세스
{: .notice--info}

## 역할
- 로그파일의 크기가 지나지게 커지는 것을 방지
- 오래된 로그파일 삭제
- **공간 절약 및 로그관리를 용이하게 함**

## Rolling 방식

### 크기 기반 Rolling
- 로그파일이 지정된 크기를 초과하면 기존 로그 파일을 벡업하고 새로운 로그파일을 생성

### 시간 기반 Rolling
- 일정 시간간격(일별, 주별, 월별)으로 새로운 로그 파일을 생성

### 혼합 기반 Rolling
- 크기  기반 Rolling 과 시간 기반 Rolling 의 혼합형태

---

# 연결문서
- [Crontab](../../servercommon/servercommon-Crontab)