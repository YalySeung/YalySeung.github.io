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

# 날짜 : 2023-10-15 23:49

# 태그 :  #하드웨어 #NAS
---

# 내용

## 설치 과정

### 하드웨어 구성
- NAS 하드웨어 조립 (하드디스크)
- LAN 및 전원 연결
- **공유기** 사용 필요

### 설치
- [시놀로지 Web Assistant 접속](https://finds.synology.com/)
  
![image](../../assets/images/SynologyConnectComplete.png)
- 설치 진행
  
![image](../../assets/images/SynologyInstall_1.png)  
![image](../../assets/images/SynologyInstall_2.png)
  
![image](../../assets/images/SynologyInstall_3.png)
  
![image](../../assets/images/DSMStarted.png)

### 설정
  
![image](../../assets/images/StartSynologyNas_1.png)
  
![image](../../assets/images/StartSynologyNas_2.png)
  
![image](../../assets/images/StartSynologyNas_3.png)
  
![image](../../assets/images/StartSynologyNas_4.png)
  
![image](../../assets/images/StartSynologyNas_5.png)
  
![image](../../assets/images/StartSynologyNas_6.png)
  
![image](../../assets/images/StartSynologyNas_7.png)
  
![image](../../assets/images/StartSynologyNas_8.png)

## DDNS 설정
  
![image](../../assets/images/IptimeSetDDNS.png)
  
![image](../../assets/images/IptimeDDNSPort.png)

## 포트 포워딩 설정
- http 프로토콜을 사용할 예정이라 5000~5005 번만 포워딩
  
![image](../../assets/images/IptimePortForwarding.png)

![image](../../assets/images/SynologyNASAddDDNS.png)

![image](../../assets/images/SynologyNASSetDNS.png)
  
![image](../../assets/images/SynologyNASSetHTTPHeader.png)

## 패키지 설치
  
![image](../../assets/images/SynologyNASInstallPackage%201.png)
  
![image](../../assets/images/SynologyNASWebDAVConfig.png)

## 모바일 연결

### File Manager Plus 다운로드
  
![image](../../assets/images/FileManagerPlusApp.png)

### 원격 서버 등록
  
![image](../../assets/images/FileManagerPlusNAS.png)

---

# 연결문서
- [DHCP](../../통신/통신-DHCP)
- [NAS](../../하드웨어/하드웨어-NAS)
- [DDNS](../../servercommon/servercommon-DDNS)
- [Port Forwarding](../../servercommon/servercommon-Port-Forwarding)