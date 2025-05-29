---
title : "Thread Dump"
excerpt : "Thread Dump"
toc : true
toc_sticky : true
toc_label : "Thread Dump"
categories:
- ServerCommon
tags:
- [ServerCommon, Java]
last_modified_at: 2023-11-24T08:00:00-10:00:00
---
  
---
  
## 📌 Thread Dump란?

> **info**
>
> Thread Dump는 JVM 프로세스 내의 모든 스레드 상태를 **Stack Trace 형태로 기록한 스냅샷**이다.  
> **데드락, 과도한 대기, CPU 점유 등 문제를 진단**하기 위한 핵심 자료로 활용된다. 
{: .notice--info}  

---
  
## ✅ Thread Dump의 구성

- 각 Thread 블록마다:
  - **Thread 이름**
  - **우선순위 및 상태**
  - **모니터 락 획득 정보**
  - **Stack Trace (호출 스택)**

예시:
```
"main" #1 prio=5 os_prio=31 tid=0x0000000101234000 nid=0x1c03 waiting on condition [0x0000000112345000]
   java.lang.Thread.State: WAITING (parking)
   at sun.misc.Unsafe.park(Native Method)
   at java.util.concurrent.locks.LockSupport.park(LockSupport.java:175)
   ...
```

---
  
## ✅ Thread 상태 분석 포인트

| 상태 | 설명 |
|------|------|
| RUNNABLE | CPU를 점유하고 실행 중 |
| WAITING | 조건이 충족될 때까지 대기 중 (`join`, `LockSupport.park`) |
| TIMED_WAITING | 특정 시간 동안 대기 (`sleep`, `wait(timeout)`) |
| BLOCKED | 락을 기다리는 중 |
| NEW | 아직 시작되지 않은 상태 |
| TERMINATED | 종료된 스레드 |

---
  
## ✅ Thread Dump 활용 시점

- CPU 사용률 급증
- 응답 지연, 서버 정지 현상 발생
- 데드락, 스레드 누수 의심
- GC 튜닝 및 성능 병목 진단

---
  
## ✅ Thread Dump 생성 방법

| 환경 | 명령어 |
|------|--------|
| 리눅스 | `kill -3 {PID}` → stdout에 출력 |
| JDK 도구 | `jstack {PID}` |
| VisualVM | Attach 후 Thread 탭에서 Dump |
| Spring Boot Actuator | `/actuator/threaddump` (관리 기능 설정 필요)

---
  
## ✅ MAT (Memory Analyzer Tool)
  
### 🔹 정의

> Eclipse Memory Analyzer Tool (MAT)은 `.hprof` 덤프 파일을 시각화 분석하는 도구이다.  
> **메모리 누수**, **GC 힙 점유 분석** 등을 정량적으로 수행할 수 있다. 
{: .notice}  

---
  
### 🔹 사용 방법

1. `.hprof` 파일을 MAT에서 열기
  
![image](../../assets/images/MATOpenHeapDump.png)

2. Dominator Tree 뷰에서 메모리 소모 객체 분석
3. 의심 객체의 **Shallow Heap** 및 **Retained Heap** 비교
  
![image](../../assets/images/MATDominator_tree.png)

---
  
### 🔹 주요 개념

| 개념 | 설명 |
|------|------|
| Shallow Heap | 단일 객체가 차지하는 메모리 |
| Retained Heap | 해당 객체로부터 참조된 모든 객체 포함한 총 메모리 |
| Outgoing Reference | 객체가 참조하는 대상들 |
| Incoming Reference | 객체를 참조하는 상위 객체들 |

---
  
# 연결문서
- [Thread](../../servercommon/servercommon-Thread)
- [JVM](../../java/java-JVM)