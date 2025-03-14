---
title : "Synology Docker"
excerpt : "Synology Docker"
toc : true
toc_sticky : true
toc_label : "Synology Docker"
categories:
- 하드웨어
tags:
- [하드웨어]
last_modified_at: 2024-11-26T08:00:00-10:00:00
---
  
---
  
 이 글에서는 Synology NAS 에 docker 환경을 구성하는 방법에 대해 알아보겠다.

 먼저 패키지 센터에서 Docker를 검색한다. Docker 패키지 또는 Container Manager 패키지를 찾아 설치를 진행한다.
  
![image](../../assets/images/SynologyDockerPackage.png)
  
![image](../../assets/images/SynologyDockerPackageInstall.png)

설치가 완료됐다면, 이제부터는 [Nginx](../../servercommon/servercommon-Nginx) 서버를 올려보자.

 Container Manager를 실행하여 레지스트리 카테고리를 선택하면 미리 만들어놓은 Docker 이미지들을 확인할 수 있다.
  
![image](../../assets/images/SynologyNASDockerImage.png)

 여기서 nginx 이미지를 더블클릭한다.
  
![image](../../assets/images/SynologyNASDockerVersion.png)

 위와 같이 버전을 선택하는 팝업창이 나타나면 latest 버전을 선택하여 진행한다.
  
![image](../../assets/images/SynologyNASDockerImageDownload.png)

 다운로드가 완료되면, 이미지를 선택하고 실행한다.
  
![image](../../assets/images/SynologyNASDockerStartImage.png)

 컨테이너 설정창이 팝업되었다. 
  
![image](../../assets/images/SynologyNASDockerSetting.png)

 포트 변경이 필요하다면, Web Station을 설치해야한다. 안내에 따라 설치를 진행하자.

> **Web Station 이란?**  
>
> 웹 사이트 호스팅 패키지로 자신의 웹사이트를 NAS에 게시할 수 있다. 
{: .notice--info}  
  
![image](../../assets/images/WebStationInstallPopup.png)

 Web Station 설치가 완료되면, 설치를 계속해서 진행한다. 필자는 리소스 제한과 웹 포털 설정을 추가했다.
  
![image](../../assets/images/SynologyNASDockerSetting2.png)

 이후 안내에 따라 설치를 진행하면 된다.
  
![image](../../assets/images/SynologyNASDockerSetting3.png)

 설치가 완료되면, 포털 만들기 마법사가 실행된다. 
  
![image](../../assets/images/SynologyWebPortal.png)

 호스트명을 설정하고 생성한다.
  
![image](../../assets/images/SynologyWebStation2.png)

---
  
# 연결문서
- [Synology NAS](../../하드웨어/하드웨어-Synology-NAS)
- [Docker](../../developcommon/developcommon-Docker)
- [Nginx](../../servercommon/servercommon-Nginx)