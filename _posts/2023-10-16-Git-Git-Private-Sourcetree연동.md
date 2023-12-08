---
title : "Git-Private-Sourcetree연동"
excerpt : "Git-Private-Sourcetree연동"
toc : true
toc_sticky : true
toc_label : "Git-Private-Sourcetree연동"
categories:
- Git
tags:
- [Git, SourceTree]
last_modified_at: 2023-10-16T08:00:00-10:00:00
---

# 날짜 : 2023-10-16 22:27

# 태그 : #Git #SourceTree 
---

# 내용

##  SSH key 생성
- [key 생성방법](../../통신/통신-SSH#git을-사용한--키-생성)

## Git Repository에 Public Key 등록
- Repository의 settings 탭에 Add deploy key 항목을 선택한다
![image](./../../assets/images/../../assets/Images/GitRepositoryAddSSHKeyMenu.png)
- 생성해뒀던 SSH public key 파일을 열어 내용을 복사한다.
![image](./../../assets/images/../../assets/Images/SSHKeyContent.png){: width=500 height=500}
- 복사한 내용을 Git Deploy Key를 입력하여 등록한다.
![image](./../../assets/images/../../assets/Images/GitAddSSHKeyContent.png){: width=500 height=500}
![image](./../../assets/images/../../assets/Images/GitSSHKeyAddResult.png){: width=500 height=500}

## SourceTree에 Public Key 등록
- 소스트리의 도구-옵션 팝업창에 SSH 키를 등록하는 항목이 있다.
![image](./../../assets/images/../../assets/Images/SourceTreeAddSSH.png){: width=400 height=400}
- [Git-Private-Sourcetree연동]() 항목에서 사용했던 .pub 파일을 등록한다.

## Repository Clone
- Git Repository에서 SSH Pull url 을 복사한다.
![image](./../../assets/images/../../assets/Images/GitSSHPullURL.png){: width=400 height=400}
- SourceTree Clone target 에 붙여넣어 Clone 한다.
![image](./../../assets/images/../../assets/Images/SourceTreeClone.png){: width=400 height=400}
---

# 연결문서
- [SSH](../../통신/통신-SSH#git을-사용한--키-생성)
- [Git-ErrorList](../../Git/Git-Git-ErrorList#ssh-rsa)