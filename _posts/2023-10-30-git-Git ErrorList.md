---
title : "Git ErrorList"
excerpt : "Git ErrorList"
toc : true
toc_sticky : true
toc_label : "Git ErrorList"
categories:
- Git
tags:
- [Git]
last_modified_at: 2023-10-30T08:00:00-10:00:00
---
  
---
  
## ssh-rsa
> **error**
>
> Unable to negotiate with xxx.xxx.xxx.xxx port 22: no matching host key type found. Their offer: ssh-rsa 
{: .notice}  
  
### 원인
- SSH 공개 키 알고리즘 중 ssh-rsa 가 활성화 되어 있지 않아서 발생하는 에러
  
### 해결방법
- ssh-rsa 알고리즘 활성화
- C:\Program Files\\Git\\etc\\ssh 경로의 ssh_config 파일 수정
```
Host *
    HostkeyAlgorithms ssh-dss,ssh-rsa
    KexAlgorithms +diffie-hellman-group1-sha1
```

---
  
# 연결문서
