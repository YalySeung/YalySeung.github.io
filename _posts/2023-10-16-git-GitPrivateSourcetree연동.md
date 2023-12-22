---
title : "GitPrivateSourcetree연동"
excerpt : "GitPrivateSourcetree연동"
toc : true
toc_sticky : true
toc_label : "GitPrivateSourcetree연동"
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

## Public Key 등록

### Repository에 등록하는법
- **특정 Repository에 대한 권한만 획득하려면 Repository에 Deploy Key를 등록한다.**
- Repository의 settings 탭에 Add deploy key 항목을 선택한다
  
![image](../../assets/images/GitRepositoryAddSSHKeyMenu.png)
- 생성해뒀던 SSH public key 파일을 열어 내용을 복사한다.
  
![image](../../assets/images/SSHKeyContent.png){: width=500 height=500}
- 복사한 내용을 Git Deploy Key를 입력하여 등록한다.
  
![image](../../assets/images/GitAddSSHKeyContent.png){: width=500 height=500}
  
![image](../../assets/images/GitSSHKeyAddResult.png){: width=500 height=500}

### Git 계정에 등록하는법
- **계정에 귀속된 모든 Repository에 대한 권한을 획득하려면 계정 SSH키 설정에 키를 등록한다.**
  
![image](../../assets/images/GitUserSetting.png)
  
![image](../../assets/images/GitUserAddSSHKey.png)

## SourceTree에 Public Key 등록
- 소스트리의 도구-옵션 팝업창에 SSH 키를 등록하는 항목이 있다.
  
![image](../../assets/images/SourceTreeAddSSH.png){: width=400 height=400}
- [Git-Private-Sourcetree연동]() 항목에서 사용했던 .pub 파일을 등록한다.

## Repository Clone
- Git Repository에서 SSH Pull url 을 복사한다.
  
![image](../../assets/images/GitSSHPullURL.png){: width=400 height=400}
- SourceTree Clone target 에 붙여넣어 Clone 한다.
  
![image](../../assets/images/SourceTreeClone.png){: width=400 height=400}
---

# 연결문서
- [SSH](../../통신/통신-SSH#git을-사용한--키-생성)
- [Git-ErrorList](../../git/git-GitErrorList#ssh-rsa)