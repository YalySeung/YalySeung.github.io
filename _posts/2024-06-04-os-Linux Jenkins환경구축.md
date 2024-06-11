---
title : "Linux Jenkins환경구축"
excerpt : "Linux Jenkins환경구축"
toc : true
toc_sticky : true
toc_label : "Linux Jenkins환경구축"
categories:
- OS
tags:
- [미완료]
last_modified_at: 2024-06-04T08:00:00-10:00:00
---
  
---
  
 먼저 jenkins 설치를 진행한다. 필자는 yum 을 사용하여 설치를 진행하였다.
  
```bash
sudo yum install jenkins
```

 /etc/sysconfig 경로에 jenkins 환경 설정 파일이 생성되었다. 접근 포트 변경이 필요하다면 먼저 jenkins 파일을 수정한다.
```
...
  
# Port Jenkins is running on
JENKINS_PORT="9703" //접근 포트

```

 그다음은 /lib/systemd/system/jenkins.service 파일을 수정한다.
```
...
  
# Port to listen on for HTTP requests. Set to -1 to disable.
  
# To be able to listen on privileged ports (port numbers less than 1024),
  
# add the CAP_NET_BIND_SERVICE capability to the AmbientCapabilities
  
# directive below.
Environment="JENKINS_PORT=9703"
...
```

 설정한 포트의 방화벽을 확인 한 후 닫혀있다면 open한다.
  
```bash
sudo iptables -L -n | grep 9703
sudo iptables -I INPUT -p tcp --dport 9703 -j ACCEPT
```

 위 과정을 모두 수행했다면 Jenkins를 실행해보겠다.
  
```bash
systemctl enable jenkins
systemctl start jenkins
```

 설정한 포트에 접속하면 반가운 메인 페이지를 만나볼 수 있다.
   
![image](../../assets/images/JenkinsMainPage.png)

 혹시 초기 비밀번호 설정 없이 로그인 페이지로 넘어간다면 비밀번호 초기화 과정을 진행한다.
/var/lib/jenkins/config.xml 파일의 보안 설정을 false로 변경하여 재시작하자
```
...
<useSecurity>false</useSecurity> 
{: .notice}  
...
```

 그러면 로그인 과정을 건너뛰고 welcome 페이지에 접속할 수 있다.
   
![image](../../assets/images/JenkinsWelcome.png)

 jenkins 관리 > Security 페이지에 접근하여 보안 설정을 변경한다. 
{: .notice}  
  
![image](../../assets/images/Pasted%20image%2020240604155214.png)
  
 이제부터는 Jenkins에 Build Item을 추가해보겠다. 일단 jekins가 git Repsitory에 접근할 때, 사용할 SSH Key를 생성해보겠다. 
  
```bash
mkdir /var/lib/jenkins/.ssh
cd /var/lib/jenkins/.ssh
```

 생성이 완료되었다면 내용을 확인한다.
  
```bash
cat github_ansible-in-action.pub
```

---
  
# 연결문서
- [Linux-방화벽및포트](../../os/os-Linux-방화벽및포트)