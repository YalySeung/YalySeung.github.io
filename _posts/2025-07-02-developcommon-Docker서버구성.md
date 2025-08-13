---
title : "Docker서버구성"
excerpt : "Docker서버구성"
toc : true
toc_sticky : true
toc_label : "Docker서버구성"
categories:
- DevelopCommon
tags:
- [SpringBoot, React, DevelopCommon]
last_modified_at: 2025-07-02T08:00:00-10:00:00
---
  
---
  
 Spring Boot 백엔드와 React 프론트엔드로 구성된 사진관리 프로젝트를 Docker 기반으로 배포하였다. 이 글에서는 Docker를 이용해 개발 환경을 구성하고 서버에 배포한 과정을 정리해 보도록 하자
  
## 서버 환경 준비
  
```bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y docker.io docker-compose openjdk-17-jdk git
```

---
  
## Spring Boot 앱 도커화

> **백엔드 앱은 Gradle로 build한 JAR 파일을 컨테이너에 복사하여 실행하는 방식으로 구성한다.**  
> 
{: .notice--info}  
  
```dockerfile
FROM openjdk:17
VOLUME /tmp
ARG JAR_FILE=build/libs/*.jar
COPY ${JAR_FILE} app.jar
ENV SPRING_PROFILES_ACTIVE=prod
ENTRYPOINT ["java","-jar","/app.jar"]
```

---
  
## React 앱 도커화

> **프론트는 Vite 기반으로 빌드한 정적 파일을 nginx에 serve하는 형태로 구성하였다.**  
> 
{: .notice--info}  
  
```dockerfile
FROM nginx:alpine
COPY ./dist /usr/share/nginx/html
COPY ./default.conf /etc/nginx/conf.d/default.conf

```  
---
  
## Docker Compose로 통합 관리

> **`docker-compose.yml`로 백엔드와 프론트엔드를 동시에 관리할 수 있도록 구성했다.**  
> 
{: .notice--info}  
  
```bash
services:
  backend:
    build:
      context: ./pictureManagerServer
      dockerfile: Dockerfile
    container_name: springboot-app
    ports:
      - "8080:8080"
    volumes:
      - /home/user/application/pictureManagerServer/photos:/app/photos
      - /home/user/application/pictureManagerServer/logs:/app/logs
    environment:
      SPRING_PROFILES_ACTIVE: prod

  frontend:
    build:
      context: ./pictureManagerClient
      dockerfile: Dockerfile
    container_name: react-nginx
    ports:
      - "3000:80"

volumes:
  db_data:

```
  
```bash
docker-compose up --build -d
  
``````

---
  
## 보안 설정 및 배포 주의사항

- DB 정보나 비밀키는 `.env` 또는 `application-secret.yml` 등 외부 파일로 분리
- nginx reverse proxy 구성 및 HTTPS 인증서(예: Let's Encrypt) 적용 필요
- 도메인 및 방화벽 설정은 운영 환경에 맞게 조정

---
  
## 마무리

 Docker를 이용해 Spring Boot와 React 앱을 분리된 컨테이너에 배포하면서 운영환경 구성의 유연성과 효율성을 확보하였다. 개발과 운영 환경을 분리해 배포 자동화로 확장할 수 있는 기반을 마련하였다.

---
  
# 연결문서
- [Docker](../../developcommon/developcommon-Docker)
- [Docker-Image](../../developcommon/developcommon-Docker-Image)
