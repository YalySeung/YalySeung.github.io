---
title : "Git SSH Config"
excerpt : "Git SSH Config"
toc : true
toc_sticky : true
toc_label : "Git SSH Config"
categories:
- Git
tags:
- [Git]
last_modified_at: 2024-04-02T08:00:00-10:00:00
---
  
---
  
> **ssh_config 파일은?**  
>
> ssh 사용시, 기타 설정을 할 수 있는 설정파일 
{: .notice--info}  
  
## ERROR
- ssh 키를 정상적으로 발급받아 Git Remote에 등록했음
- ssh 로 clone, fetch 시 **no matching host key type found. Their offer: ssh-rsa,ssh-dss** 에러 발생

> **error**
>
> 15:41:51.254: [TestRepository] git -c credential.helper= -c core.quotepath=false -c log.showSignature=false fetch origin --recurse-submodules=no --progress --prune 
{: .notice--info}  
Unable to negotiate with 61.109.169.13 port 29418: no matching host key type found. Their offer: ssh-rsa,ssh-dss
  
## SOLVE
- ssh_config 파일에 HostKeyAlgorithm 추가
  
![image](../../assets/images/ssh_configPath.png)
  
```bash
...
Host 61.109.169.13
    HostKeyAlgorithms +ssh-rsa,ssh-dss
...
```

---
  
# 연결문서
- [Intellij](../../ide/ide-Intellij)