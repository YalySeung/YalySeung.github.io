---
title : "nvidia smi"
excerpt : "nvidia smi"
toc : true
toc_sticky : true
toc_label : "nvidia smi"
categories:
- DevelopCommon
tags:
- [Linux, GPU, NVIDIA, Server, CLI]
last_modified_at: 2026-03-17T08:00:00-10:00:00
---
  
---
  
## 📌 nvidia-smi란?

> **info**
>
> `nvidia-smi` 는 NVIDIA GPU 상태를 확인하고 관리할 수 있는 **CLI(Command Line Interface) 도구**이다. 
{: .notice--info}  

 GPU 사용률, 메모리 사용량, 실행 중인 프로세스 등을 확인할 수 있으며 AI 서버나 CUDA 환경에서 필수적으로 사용된다.

---
  
## 📌 기본 명령어
  
```bash
nvidia-smi
```

 GPU 상태를 한 번 조회한다.

---
  
## 📌 주요 정보

| 항목 | 설명 |
|-----|-----|
| GPU Name | GPU 모델 |
| Temp | GPU 온도 |
| Pwr | 전력 사용량 |
| Memory Usage | GPU 메모리 사용량 |
| GPU-Util | GPU 사용률 |

---
  
## 📌 실시간 모니터링
  
```bash
watch -n 1 nvidia-smi
```

 1초 간격으로 GPU 상태 확인

---
  
## 📌 GPU 상세 정보
  
```bash
nvidia-smi -q
```

 GPU 상세 상태 조회

---
  
## 📌 GPU 사용률 모니터링
  
```bash
nvidia-smi dmon
```

 GPU 연산 / 메모리 사용률 확인

---
  
# 연결 문서