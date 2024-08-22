---
title : "Git Bash CLI"
excerpt : "Git Bash CLI"
toc : true
toc_sticky : true
toc_label : "Git Bash CLI"
categories:
- Git
tags:
- [Git, CLI]
last_modified_at: 2023-12-14T08:00:00-10:00:00
---
  
---
  
## 설정 정보
  
### 설정 정보 확인
  
```bash
git config --list
```
  
### 사용자명 변경
  
```bash
git config --global user.name <사용자명>
```
  
### 이메일 주소 변경
  
```bash
git config --global user.email <이메일주소>
```
  
### 계정정보 삭제
  
```bash
git config --unset user.name
git config --unset user.email
```
  
### 브랜치 관리
  
```bash
git branch -r // 원격 저장소 브랜치 조회
git push origin --delete <브랜치명> // 원격 저장소 브랜치 삭제

```
  
## SSH
  
### ssh key 생성
```
ssh-keygen
```
  
---
  
# 연결문서
- [SSH](../../통신/통신-SSH)