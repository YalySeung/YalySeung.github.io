---
title : "Linux Command Detail"
excerpt : "Linux Command Detail"
toc : true
toc_sticky : true
toc_label : "Linux Command Detail"
categories:
- CLI
tags:
- [CLI, Linux]
last_modified_at: 2023-11-08T08:00:00-10:00:00
---

# 날짜 : 2023-11-08 14:41

# 태그 : #CLI #Linux 
---

# 내용

## 명령어

### JVM heap 메모리 사용량 확인

```bash
jmap -heap <pid>
```

### top

```bash
top
```
  
![image](../../assets/images/LinuxTopResult.png)

#### Summary Region
- 전체 프로세스가 OS에 대해서 리소스를 어느정도 차지하는지 표시
- system time, up time, user
- Load Average
- Task
- CPU
- Memory

#### Detail Region
- 각 Task 별 상세내역 표시

##### PID
- 프로세스 ID

##### USER
- 해당 프로세스를 실행한 User 또는 효과를 받는 User

##### PR & NI
- PR : 커널에 의해서 스케쥴링 되는 우선순위
- NI : PR에 영향을 주는 nice 값

##### VRIT
- 프로세스가 소비하고 있는 총 메모리
- 프로그램이 실행중인 코드, heap, stack과 같은 메모리, IO buffer 메모리를 포함

##### RES
- RAM에서 사용중인 메모리의 크기

##### SHR
- 다른 프로세스와의 공유메로리를 나타냅니다.

##### %MEM
- RAM에서 RES가 차지하는 비율

##### S
- 프로세스의 현재 상태

##### TIME+
- 프로세스가 사용한 토탈 CPU 시간

##### COMMAND
- 해당 프로세스가 실행한 커맨드

#### 보고싶은 순으로 정렬
- shift + m : 메모리 사용량 순으로 정렬
- shift + p : CPU 사용량 순으로 정렬
- shift + n : process id 로 정렬
- shift + t : running time 순으로 정렬
- shift R : 오름차순과 내림차순을 토글 변경

### shutdown
- 서버 종료 후 **재부팅**

#### 종료

```bash
shutdown -h now 
```

---

# 연결문서
- [CLI](../../cli/cli-CLI)
- [CLI-BaseCommand](../../cli/cli-CLI-BaseCommand)