---
title : "Docker"
excerpt : "Docker"
toc : true
toc_sticky : true
toc_label : "Docker"
categories:
- DevelopCommon
tags:
- [DevelopCommon]
last_modified_at: 2024-07-10T08:00:00-10:00:00
---
  
---
  
> **Docker란?**  
>
> Go 언어로 작성된 리눅스 컨테이너 기반의 오픈소스 가상화 플랫폼이다. 
{: .notice--info}  
  
## 가상화
 서버 관리자들은 서버 컴퓨터의 CPU 성능의 10%밖에 쓰지 못하는 리소스 낭비를 줄일 필요성을 느낄 것이다. 그렇다고 모든 솔루션을 한 서버에 올리는 것은 리스크가 너무 크기 때문에 가상화 솔루션 사용한다.
  
![image](../../assets/images/VirtualEnvironment.png)

 위 이미지에서 보다시피 **전통적인 방식**으로는 하나의 물리서버에 여러 앱을 올려서 사용할 수 있지만, 저장 공간 자체를 공유하기 때문에 **라이브러리나 미들웨어 간 충돌이 발생 할 수 있다**. 또한 하나의 애플리케이션이 가질 수 있는 리소스의 한계를 정의할 수 없다. 그렇기 때문에 **리소스를 과다 사용하는 애플리케이션이 다른 애플리케이션의 성능 저하를 유발**한다. 그렇다고 하나의 애플리케이션만 사용하기에는 CPU, Memory 리소스 낭비가 발생한다.

 반면 **VM 방식**은 Host OS 위에 가상화 소프트웨어인 **Hypervisor**를 설치하여 환경을 구축한다. 각 **가상 환경은 분리되어 있어 일정 수준의 보안성을 제공**한다. 그리고 가상 환경의 리소스를 제한할 수 있어 **리소스를 효율적으로 사용하고, 비용을 절감**할 수 있다. 반면에, 가상 환경에 존재하는 Guest OS는 용량을 많이 차지하고, 불필요한 기능도 가지고 있으며, OS 자체가 자원을 많이 점유하기 때문에 **느리다는 단점**이 있다.

 **Container 방식**은 VM 방식에서 좀 더 발전하여 **Container Runtime 위에 Guest OS 없이 애플리케이션이 올라간다**. Container에서 OS가 실행되지만 애플리케이션이 동작할 정도의 최소 기능만 동작하기 때문에 **속도 측면에서 이점이 있다**. Container 방식을 사용하면 서버 한대에서 여러 응용프로그램을 사용하여 **마이크로 서비스 구조의 서버를 구축**할 수 있다. 뿐만 아니라 커널 하나로 모든 컨테이너들을 관리하므로 **관리가 쉽다**.
  
## 주요 개념
 Docker에서 사용되는 주요 개념들에 대해서 알아보자.
 
 Docker에서 애플리케이션과 그 실행 환경을 포함하는 표준화된 소프트웨어 유닛을 **Container**라고 하는데, 이 Container는 호스트 시스템의 커널을 공유하지만, 애플리케이션과 그 의존성을 독립적으로 격리하여 실행 할 수 있다. (리눅스의 Container와는 조금 다르다.)

 이 Container를 생성하기 위해서는 애플리케이션 코드, 라이브러리, 종속성 등을 포함하는 읽기 전용 템플릿이 필요한데, 이것을 **Image**라고 부른다.

 Image를 생성하기 위해서는 **Dockerfile**이라는 설정파일이 필요하며, Image의 빌드 과정과 내용을 기술한다. 이를 통해 Image 빌드 과정이 자동화 된다.

 Docker 이미지를 저장하고 공유할 수 있는 퍼블릭 레지스트리를 **Docker Hub**라고 하는데, 여기서 이미지를 업로드하고 다운로드 할 수 있다.
  
## Docker 환경 구축
  
### 1. Hyper-V 활성화
 Docker 사용에 필요한 가상화 기술인 Hyper-V를 활성화 해보자. 일단 작업 관리자 > 성능 탭에서 가상화 여부를 확인한다. 사용 안 함으로 되어있을 경우 BIOS에서 사용으로 설정해야 한다. 
{: .notice--info}  
   
![image](../../assets/images/AdministratorVirtualCheck.png)

 그 다음으로 제어판 > 프로그램 설치 및 제거 > Window 기능 켜기/끄기 에서 Hyper-V 기능을 체크한다.  
{: .notice}  
 
> **caution**
> 
{: .notice}  
 MS 공식 문서를 보면 Hyper-V 기능은 Windows 10(Enterpirse, Pro, Education)에서 지원한다.
  
### 1. Docker 설치
 먼저 Docker 를 다운받아 설치하는 것부터 시작해보자. 다운로드는 [공식 홈페이지 다운로드](https://docs.docker.com/desktop/install/windows-install/) 페이지를 이용한다.
  
---
  
# 연결문서
- [VirtualBox](../../developcommon/developcommon-VirtualBox)