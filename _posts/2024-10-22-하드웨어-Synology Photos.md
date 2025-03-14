---
title : "Synology Photos"
excerpt : "Synology Photos"
toc : true
toc_sticky : true
toc_label : "Synology Photos"
categories:
- 하드웨어
tags:
- [하드웨어, NAS]
last_modified_at: 2024-10-22T08:00:00-10:00:00
---
  
---
  
 이 글에서는 Synology NAS 에 사진을 벡업할 수 있는 Synology Photos 제품에 대해서 알아보고 환경을 구성해 보겠다.

> **Synology Photos란?**  
>
> Synology(시놀로지)에서 제공하는 사진 관리 및 저장 솔루션으로, Synology NAS(Network Attached Storage) 장치에서 작동하는 애플리케이션이다. 
{: .notice--info}  
  
## Synology Photos 설치
 [Synology NAS](../../하드웨어/하드웨어-Synology-NAS) 의 기본 설정을 완료했다면, Synology Photos 패키지를 설치하고 모바일과 연동을 진행하자.

 패키지 센터에서 Synology Photos를 검색하여 설치를 진행한다.
  
![image](../../assets/images/SynologyPhotos_Install.png)

 설지가 완료되면 NAS 바탕화면에 아이콘이 생성된다. 아이콘을 클릭하면 Synology Photos 페이지에 접속할 수 있다.
  
## Synology Photos 설정
 설치가 완료되었다면 설정을 진행해보자. Synology Photos 페이지의 설정 > 공유 장소 > 공유 장소 활성화 > 액세서 권한 설정 에서 사용자 정보를 할당해준다.
  
![image](../../assets/images/SynologyPhotos_Config.png)
  
## 모바일 설정
 이제 모바일 앱을 설치하여 NAS와 연동해보자
  
![image](../../assets/images/SynologyPhotos_Mobile.png)

 위 앱을 다운로드 받아 실행시킨다. 이후 앱을 실생하여 NAS 이름과 계정으로 접속한다.
  
![image](../../assets/images/KakaoTalk_20240903_175946910.jpg)

 설정에서 사진 벡업 옵션을 활성화하면, NAS 서버로 벡업이 진행된다.

---
  
# 연결문서
- [Synology NAS](../../하드웨어/하드웨어-Synology-NAS)