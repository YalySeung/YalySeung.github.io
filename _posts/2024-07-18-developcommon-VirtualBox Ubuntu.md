---
title : "VirtualBox Ubuntu"
excerpt : "VirtualBox Ubuntu"
toc : true
toc_sticky : true
toc_label : "VirtualBox Ubuntu"
categories:
- DevelopCommon
tags:
- [DevelopCommon]
last_modified_at: 2024-07-18T08:00:00-10:00:00
---
  
---
  
> **VirtualBox 란?**  
>
> Oracle Corporation에서 개발한 오픈소스 가상화 소프트웨어로 가상 컴퓨터를 만들고 관리하는 데 널리 사용된다. 
{: .notice--info}  
  
## VirtualBox 환경 셋팅
 필자는 Ubuntu Server OS 22.04를 사용하겠다.
  
### 1. Ubuntu 이미지 다운로드
 VirtualBox에 넣을 ISO 이미지 파일을 [Ubuntu 공식 홈페이지](https://releases.ubuntu.com/22.04/?_gl=1*1xraa55*_gcl_au*MTU1NDE3NzAwNS4xNzIwNzU5MzY2&_ga=2.71321488.2082941696.1721286058-1657586646.1720759364)에서 다운로드 한다.
  
### 2. VirtualBox 다운로드 및 설치
 그 다음  [VirtualBox 공식 홈페이지](https://www.virtualbox.org/wiki/Downloads)에서 다운로드를 진행한다. 필자는 Window OS를 사용중으로 Window 버전을 다운로드 받았다. 다운로드가 완료 되었다면, 설치를 진행한다.
  
### 2. 가상 머신 추가
 이제부터 가상 머신을 추가해보자.
   
![image](../../assets/images/VirtualBoxInstall_1.png)

 Virtual Box에서 새로 만들기 버튼을 선택한다.
  
![image](../../assets/images/VirtualBoxInstall_2.png)

 가상 머신의 이름을 입력하고, 위에서 받아뒀던 Ubunbu iso 이미지 파일을 추가한다.
  
![image](../../assets/images/VirtualBoxInstall_3.png)

 가상 머신에 할당할 메모리 크기를 정한다. 통상 내 로컬 PC의 반정도를 할당하지만 필자는 간단한 서비스 하나 정도만 올릴 예정이기 때문에 2G만 할당하겠다.
  
![image](../../assets/images/Pasted%20Image%2020240718162545_809.png)
  
![image](../../assets/images/Pasted%20Image%2020240718162600_821.png)

 언어 선택 및 업데이트 설정 이후 과정은 Done 으로 넘기면 된다.

> **caution**
>
> 설치가 완료되기 전에 VM을 종료하면 OS를 다시 설치해야 한다. 꼭 설정이 완료되었는지 확인하고 종료하도록 하자. 
{: .notice--info}  
  
![image](../../assets/images/Pasted%20Image%2020240718162727_536.png)

 설정이 완료되면 위와 같은 터미널을 볼 수 있다.
  
### 3. 계정 설정
 [SSH](../../통신/통신-SSH) 화면으로 돌아와 root 계정의 비밀번호를 설정해보자. 필자는 root 계정 비밀번호 설정을 까먹어서 고생한 경험이 있으니 빠뜨리지 말고 진행해야 하는 과정이다. 

 먼저 root 계정의 비밀번호를 설정한다.
  
```bash
sudo passwd root
```
  
### 4. [SSH](../../통신/통신-SSH) 설정
 루트 계정 생성까지 마쳤다면, 외부에서 ssh로 접근할 수 있도록 설정을 해야한다. vm의 ip를 확인하자.
 
 > **tip**
> 
{: .notice--info}  
 >  virtual box에 게스트 확장을 적용하여 기타 기능들을 사용할 수 있지만 MobaXterm이나 putty로 접속하여 사용하는 것이 건강에 이롭다.
  
```bash
ifconfig
```

 Command가 없다면 net tools을 설치한다.
  
```bash
sudo apt install net-tools
```
  
![image](../../assets/images/UbuntuIPAddress.png)
  
### 5. 포트 포워딩

> **포트 포워딩이란 ?**  
>
> 특정 포트 번호를 통해 하나의 IP 주소에서 다른 IP주소로 네트워크 트래픽을 전달하는 프로세스를 말한다. 
{: .notice--info}  

 가상 환경 구성이 완료되었지만 아직 할 일이 남아있다. 외부에서 내 PC의 특정 포트로 들어오는 요청을 가상 머신으로 전달하려면 [Port Forwarding](../../servercommon/servercommon-Port-Forwarding)이 필요하다. 

 위에서 확인한 ip로 port forwarding 설정을 한다.
  
![image](../../assets/images/VirtualBox_PortForwarding.png)
  
![image](../../assets/images/VirtualBox_PortForwarding_2.png)

 ssh 접근을 위한 포트와 필자가 사용 예정인 mariadb port를 추가했다. mariadb 포트는 로컬에 설치된 mariadb와의 충돌을 막기위해 3309포트로 잡았다.

 외부 ssh 툴로 접속할 수 있다.
  
![image](../../assets/images/VirtualBox_MobaXtermSSH.png)

---
  
# 연결문서
- [Docker](../../developcommon/developcommon-Docker)
- [Ubuntu-MariaDB설치-Online](../../os/os-Ubuntu-MariaDB설치-Online)