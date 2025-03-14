---
title : "Synology NAS"
excerpt : "Synology NAS"
toc : true
toc_sticky : true
toc_label : "Synology NAS"
categories:
- 하드웨어
tags:
- [하드웨어, NAS]
last_modified_at: 2023-10-15T08:00:00-10:00:00
---
  
---
  
 이 글에서는 Synology NAS의 초기 환경 세팅 과정을 다루겠다. 

 개인 NAS 서버를 구성하기 위해서는 **Case**, **하드디스크**, **공유기**가 필요하다. 필자는 처음에 공유기가 아닌 Hub를 사용하여 삽질 한 경험이 있으니 주의가 필요함을 당부한다.

 하드웨어 준비가 완료됐다면 설치를 진행해보겠다. 설치 과정은 아래와 같다.
  
## Synology NAS 설치
 첫번째로 해야 할 일은 [시놀로지 Web Assistant 접속](https://finds.synology.com/)하여 하드웨어 구성이 제대로 됐는지 확인해야 한다. 아래와 같은 이미지가 보인다면 정상적으로 연결된 것이다.
  
![image](../../assets/images/SynologyConnectComplete.png)

 이후로는 Web Assistant가 인도하는대로 설치를 진행한다.
  
![image](../../assets/images/SynologyInstall_1.png)  
![image](../../assets/images/SynologyInstall_2.png)
  
![image](../../assets/images/SynologyInstall_3.png)
  
![image](../../assets/images/DSMStarted.png)

 설치가 완료되었다면 초기 정보 입력 화면이 보일 것이다. 이 역시 아래 순서로 진행해준다.
  
![image](../../assets/images/StartSynologyNas_1.png)
  
![image](../../assets/images/StartSynologyNas_2.png)
  
![image](../../assets/images/StartSynologyNas_3.png)
  
![image](../../assets/images/StartSynologyNas_4.png)
  
![image](../../assets/images/StartSynologyNas_5.png)
  
![image](../../assets/images/StartSynologyNas_6.png)
  
![image](../../assets/images/StartSynologyNas_7.png)
  
![image](../../assets/images/StartSynologyNas_8.png)
  
## 외부 접속을 위한 NAS 고정 IP 설정
 NAS 서버 구성이 완료 되었다면, 외부에서 접근 제어판 > 네트워크 > 네트워크 인터페이스 > 편집 > IPv4 메뉴에서 IP 설정을 변경한다. Synology NAS 의 기본 IP 설정은 [DHCP](../../통신/통신-DHCP) 로 되어있다. 이것을 수동 구성으로 변경하고 내부 IP 중 사용 빈도가 없는 IP 로 설정한다. 필자는 192.168.0.254로 설정했다.
  
![image](../../assets/images/SynologyNAS_IP.png)
  
## NAS [SSH](../../통신/통신-SSH) 설정
 외부에서 SSH로 접속이 가능하도록 옵션을 활성화 한다. 제어판 > 터미널 및 SNMP 탭에서 SSH 서비스를 체크한다.
  
![image](../../assets/images/SynologySSH.png)

 SSH로 NAS에 접속하면, 관리자 계정이 root로 되어있다. 우리 NAS는 admin 계정을 사용하는데 root는 어디서 나온걸까? 사실 NAS의 admin 계정도 root 계정의 권한을 우회하여 사용한다. 

 SSH에서 관리자 권한을 얻기위해 아래와 같은 명령어를 입력한다.
  
```bash
sudo -i
//이후 비밀번호 입력
```
  
## iptime 포트 포워딩 설정
 외부의 요청을 Synology로 전달하기 위해 [Port Forwarding](../../servercommon/servercommon-Port-Forwarding) 설정을 하겠다. 먼저 웹 브라우저에서 192.168.0.1에 접속한다.
  
![image](../../assets/images/iptime_main.png)

 관리자로 로그인 후 NAT/라우터 관리 > 포트포워드 설정 메뉴에서 SSH 포트와 NAS HTTP 포트를 포워딩 한다.
  
![image](../../assets/images/iptime_portforwarding.png)
 
---
  
# 연결문서
- [DHCP](../../통신/통신-DHCP)
- [NAS](../../하드웨어/하드웨어-NAS)
- [DDNS](../../servercommon/servercommon-DDNS)
- [Port Forwarding](../../servercommon/servercommon-Port-Forwarding)
- [Port](../../developcommon/developcommon-Port#자주-사용되는-포트)