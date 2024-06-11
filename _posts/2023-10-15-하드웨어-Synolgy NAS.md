---
title : "Synolgy NAS"
excerpt : "Synolgy NAS"
toc : true
toc_sticky : true
toc_label : "Synolgy NAS"
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
  
## DDNS 설정
 설치가 완료되었다면 외부에서 접속이 가능하도록 DDNS를 설정해야 한다.
  
![image](../../assets/images/IptimeSetDDNS.png)
  
![image](../../assets/images/IptimeDDNSPort.png)
  
## 포트 포워딩 설정
 http 프로토콜을 사용할 예정이라 5000~5005 번만 포워딩 한다.
  
![image](../../assets/images/IptimePortForwarding.png)
  
![image](../../assets/images/SynologyNASAddDDNS.png)
  
![image](../../assets/images/SynologyNASSetDNS.png)
  
![image](../../assets/images/SynologyNASSetHTTPHeader.png)
  
## 패키지 설치
 외부에서 접근 가능하도록 도와주는 WebDAV Server 패키지를 설치한다.
  
![image](../../assets/images/SynologyNASInstallPackage%201.png)
  
![image](../../assets/images/SynologyNASWebDAVConfig.png)
  
## 모바일 연결
 모바일에서 NAS 서버에 접근하기 위해서 **File Manager Plus** 앱을 사용하였다.
  
![image](../../assets/images/FileManagerPlusApp.png)

 앱을 실행 한 뒤 NAS 서버 호스트와 포트 정보를 아래 이미지와 같이 입력해주면 연결이 가능하다.
  
![image](../../assets/images/FileManagerPlusNAS.png)
  
---
  
# 연결문서
- [DHCP](../../통신/통신-DHCP)
- [NAS](../../하드웨어/하드웨어-NAS)
- [DDNS](../../servercommon/servercommon-DDNS)
- [Port Forwarding](../../servercommon/servercommon-Port-Forwarding)