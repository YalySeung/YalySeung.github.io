---
title : "Docker"
excerpt : "Docker"
toc : true
toc_sticky : true
toc_label : "Docker"
categories:
- DevelopCommon
tags:
- [DevOps, DevelopCommon]
last_modified_at: 2025-06-09T08:00:00-10:00:00
---
  
---
  
## 📌 Docker란?

> **info**
>
> Go 언어로 작성된 리눅스 컨테이너 기반의 오픈소스 가상화 플랫폼이다.  
> Docker는 컨테이너 기반의 애플리케이션 배포, 이식, 실행을 자동화한다. 
{: .notice--info}  

---
  
## ✅ 가상화 개념 비교
  
### 🔹 전통적인 방식
- 여러 앱이 동일한 OS를 공유 → 라이브러리 충돌, 리소스 경쟁 가능
  
### 🔹 VM (가상 머신) 방식
- Hypervisor 위에 여러 OS 실행  
- 보안성 및 자원 격리 우수하지만 속도 느림, Guest OS 자원 낭비
  
### 🔹 Container 방식
- Guest OS 없이 애플리케이션이 올라감
- 경량화 + 빠른 실행 속도 + 커널 공유 관리 용이
- 마이크로서비스 아키텍처에 적합

---
  
## ✅ 주요 개념 요약

| 개념 | 설명 |
|------|------|
| **Image** | 애플리케이션 실행 환경을 포함한 읽기 전용 템플릿 |
| **Container** | Image를 기반으로 생성된 실행 환경 인스턴스 |
| **Dockerfile** | 이미지를 자동으로 빌드하기 위한 설정 스크립트 |
| **Docker Hub** | 이미지 저장 및 공유를 위한 중앙 레지스트리 |
| **Compose** | 여러 컨테이너를 동시에 정의하고 실행하는 도구 |

---
  
## ✅ Docker 환경 구축 (Windows 기준)

1. **Hyper-V 활성화**
   - BIOS에서 가상화 기능 활성화 필요
   - 제어판 → Windows 기능 → Hyper-V 체크

2. **Docker 설치**
   - [공식 설치 링크](https://docs.docker.com/desktop/install/windows-install/)

---
  
## ✅ Dockerfile 이란?

> Dockerfile은 Docker 이미지를 만들기 위한 명령어 스크립트 파일이다.  
> 애플리케이션 실행 환경을 코드로 정의하여 이식성과 자동화를 확보한다. 
{: .notice}  
  
### 📄 예시 (Spring Boot)
  
```Dockerfile
FROM openjdk:17-jdk-alpine
WORKDIR /app
COPY build/libs/app.jar app.jar
ENTRYPOINT ["java", "-jar", "app.jar"]
```

| 명령어 | 설명 |
|--------|------|
| `FROM` | 베이스 이미지 지정 |
| `WORKDIR` | 작업 디렉토리 설정 |
| `COPY` | 로컬 파일을 이미지에 복사 |
| `ENTRYPOINT` | 컨테이너 시작 시 실행 명령 |

---
  
## ✅ docker-compose.yml 이란?

> Docker Compose는 여러 컨테이너를 YAML 파일 하나로 정의하고 실행할 수 있도록 해주는 도구이다. 
{: .notice}  
  
### 📄 예시
  
```yaml
version: "3.8"
services:
  app:
    build:
      context: .
      dockerfile: Dockerfile
    ports:
      - "8080:8080"
    environment:
      SPRING_PROFILES_ACTIVE: prod
    volumes:
      - ./logs:/app/logs

  db:
    image: mysql:8.0
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: rootpw
      MYSQL_DATABASE: appdb
    ports:
      - "3306:3306"
    volumes:
      - dbdata:/var/lib/mysql

volumes:
  dbdata:
```

| 키워드 | 설명 |
|--------|------|
| `services` | 컨테이너 정의 |
| `build` | Dockerfile 경로 지정 |
| `image` | Docker Hub 이미지 사용 |
| `ports` | 포트 포워딩 설정 |
| `volumes` | 데이터 유지 설정 |
| `environment` | 환경변수 지정 |

---
  
# 연결문서
- [Docker]()
- [Docker-Image](../../developcommon/developcommon-Docker-Image)
- [VirtualBox-Ubuntu](../../developcommon/developcommon-VirtualBox-Ubuntu)
- [Synology Docker](../../하드웨어/하드웨어-Synology-Docker)