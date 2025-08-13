---
title : "Docker Image"
excerpt : "Docker Image"
toc : true
toc_sticky : true
toc_label : "Docker Image"
categories:
- DevelopCommon
tags:
- [DevelopCommon, DevOps]
last_modified_at: 2025-06-09T08:00:00-10:00:00
---
  
---
  
## 📌 Docker Image란?

> **info**
>
> Docker Image는 컨테이너를 생성하기 위한 **불변의 실행 환경 스냅샷**이다.  
> 애플리케이션 실행에 필요한 코드, 라이브러리, 설정 등을 포함한 읽기 전용 템플릿이다. 
{: .notice--info}  

---
  
## ✅ 이미지 vs 컨테이너

| 구분    | Image                  | Container                  |
| ----- | ---------------------- | -------------------------- |
| 개념    | 실행 환경의 템플릿             | 실제 실행 인스턴스                 |
| 특성    | 불변(Read-Only)          | 변경 가능(Read-Write Layer 포함) |
| 저장 위치 | 로컬/레지스트리(Docker Hub 등) | 메모리 및 디스크에 생성              |
| 실행 여부 | 실행 불가                  | 실행 가능                      |

---
  
## ✅ 이미지 구성 계층 (Layered Structure)

- 이미지 = 여러 개의 레이어(layer)로 구성됨
- 각 레이어는 `Dockerfile`의 명령어 하나에 대응됨
- **변경된 레이어만 캐시하고 재사용**함으로써 빌드 성능 최적화 가능

```
[Layer 4] RUN apt install curl
[Layer 3] COPY . .
[Layer 2] WORKDIR /app
[Layer 1] FROM openjdk:17
```

---
  
## ✅ 이미지 생성 및 관리 명령어

| 명령어 | 설명 |
|--------|------|
| `docker build -t [name] .` | 현재 디렉토리의 Dockerfile로 이미지 생성 |
| `docker images` | 로컬에 저장된 이미지 목록 확인 |
| `docker rmi [image_id]` | 이미지 삭제 |
| `docker pull [image]` | 외부 레지스트리에서 이미지 가져오기 |
| `docker push [image]` | 이미지 레지스트리에 업로드 |

---
  
## ✅ 이미지 저장소 (Registry)

| 유형 | 설명 |
|------|------|
| Docker Hub | 기본 공개 레지스트리, 무료 |
| GitHub Container Registry | GitHub에서 제공 |
| Private Registry | 사내 전용 이미지 저장소 구성 가능 |
  
```bash
  
# Docker Hub 로그인
docker login
  
# 사용자이름/이미지명 형식으로 push
docker tag my-app myuser/my-app
docker push myuser/my-app
```

---
  
## ✅ 이미지 최적화 팁

- 불필요한 레이어 최소화 (멀티 스테이지 빌드)
- `.dockerignore`로 빌드 제외 파일 지정
- 캐시 재사용을 위한 명령 순서 최적화
- Alpine 기반 경량 이미지 사용 권장

---
  
# 연결문서
- [Docker](../../developcommon/developcommon-Docker)