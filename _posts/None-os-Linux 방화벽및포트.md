---
title : "Linux 방화벽및포트"
excerpt : "Linux 방화벽및포트"
toc : true
toc_sticky : true
toc_label : "Linux 방화벽및포트"
categories:
- OS
tags:
- [OS, Linux]
last_modified_at: NoneT08:00:00-10:00:00
---
udo  날짜 : 2024-05-23 12:05
  
---
  
  이 글에서는 리눅스 포트와 방화벽을 여는 방법을 알아보겠다.
  
## 포트 열기
  
```bash
sudo netstat -tlnp | grep 3306
sudo ufw status // 방화벽 상태 확인
sudo ufw allow 3306/tcp // 방화벽 열기
```

 3306 포트가 열려있는지 확인 후 포트를 여는 [CLI](../../cli/cli-CLI)이다.
  
## 방화벽 열기
 방화벽을 여는 방법은 iptables를 사용하는 방법과 firewall를 사용하는 방법이 있다.
  
```bash
sudo iptables -L -n | grep 3306
sudo iptables -I INPUT -p tcp --dport 3306 -j ACCEPT
```
 위 [CLI](../../cli/cli-CLI) 는 3306 방화벽을 체크한 후 여는 [CLI](../../cli/cli-CLI)이다.
  
```bash
sudo firewall-cmd --permanent --add-port=<포트번호>/tcp 
{: .notice}  
sudo firewall-cmd --reload
```
 firewall-cmd 를 사용하는 방법은 reload 과정이 필요하다.
  
## 방화벽 설정 정보 영구 저장
 OS 재부팅시에도 설정정보를 유지하려면 iptables-services를 사용하자. **firewalld** 가 활성화되어 있으면 iptables 서비스가 동작 안 할 수 있으므로 종료한다.
  
```bash
systemctl stop firewalld
systemctl mask firewalld
```
  
```bash
sudo yum install iptables-services //서비스 설치
sudo systemctl enable iptables //방화벽 정보관리 서비스 활성화
sudo systemctl start iptables //방화벽 정보관리 서비스 실행

//필요한 방화벽 open 후

sudo iptables-save //방화벽 정보 저장
```
  
---
  
# 연결문서
