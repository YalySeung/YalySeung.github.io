---
title : "Git-Rebase"
excerpt : "Git-Rebase"
toc : true
toc_sticky : true
toc_label : "Git-Rebase"
categories:
- Git
tags:
- [Git]
last_modified_at: 2023-11-01T08:00:00-10:00:00
---

# 날짜 : 2023-11-01 13:18

# 태그 : #Git
---

# 내용

## Rebase란
- 두 개의 공통 Base를 가진 Branch에서 한 Branch의 Base를 다른 Branch의 최신 커밋으로 옮기는 작업

### Rebase 전
  
![image](../../assets/Images/Git-Rebase-Before.png)

### Rebase 후
  
![image](../../assets/Images/Git-Rebase-After.png)

## 장점
- 공유 Branch의 최신 변경사항을 즉각 반영할 수 있다.
- 커밋 이력을 남기지 않아 commit history가 깔끔해진다.

## 프로세스
- 충돌이 없다면 소스 merge
- 충돌 발생시, 각 commit 마다 conflict를 해결

---

# 연결문서
