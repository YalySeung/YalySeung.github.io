---
title : "Thread"
excerpt : "Thread"
toc : true
toc_sticky : true
toc_label : "Thread"
categories:
- ServerCommon
tags:
- [ServerCommon, Java]
last_modified_at: 2023-11-24T08:00:00-10:00:00
---
  
---
  
## 📌 Thread란?

> **info**
>
> Thread는 프로세스 안에서 **실질적으로 작업을 실행하는 흐름의 최소 단위**이다.  
> 하나의 프로세스 내에서 여러 스레드를 생성하여 **병렬 처리 및 자원 공유**가 가능하다. 
{: .notice--info}  

---
  
## ✅ Thread 종류
  
### 🔹 Non-Daemon Thread

- 일반 사용자 스레드
- 모든 Non-Daemon 스레드가 종료되어야 JVM이 종료됨
- 예: `main()` 메서드를 실행하는 기본 스레드
  
### 🔹 Daemon Thread

- 보조 작업을 수행하는 스레드 (예: Garbage Collector)
- Non-Daemon 스레드가 종료되면 자동 종료됨
- 백그라운드에서 실행되며 사용자 요청 직접 처리 X

---
  
## ✅ Thread 생명주기 (LifeCycle)
  
![image](../../assets/images/JavaThreadLifeCycle.png)

1. **NEW**: 스레드 객체 생성 상태 (`new Thread()`)
2. **RUNNABLE**: `start()` 호출 후 실행 대기
3. **RUNNING**: `run()` 메서드 실행 중
4. **BLOCKED**: 락을 획득하지 못하고 대기 중
5. **WAITING**: 조건이 충족될 때까지 무기한 대기
6. **TIMED_WAITING**: 지정된 시간 동안 대기 (`sleep()`, `join(timeout)`)
7. **TERMINATED**: 실행 종료

> **note**
>
> `sleep()`, `wait()`, `join()` 등은 상태 전이에 영향을 미친다. 
{: .notice--info}  

---
  
## ✅ Thread 상태 요약

| 상태 | 설명 |
|------|------|
| NEW | 스레드 객체 생성됨, 아직 실행되지 않음 |
| RUNNABLE | 실행 가능 상태, 스케줄러 대기 중 |
| RUNNING | 실제 CPU 자원을 받아 실행 중 |
| BLOCKED | 다른 스레드가 락을 점유 중이라 대기 |
| WAITING | 무기한 대기 (다른 스레드의 신호 필요) |
| TIMED_WAITING | 제한 시간 동안 대기 |
| TERMINATED | 실행 종료 상태 |

---
  
## ✅ Thread 우선순위
  
```java
public final static int MIN_PRIORITY = 1;
public final static int NORM_PRIORITY = 5;
public final static int MAX_PRIORITY = 10;
```

- 스케줄링 순서에 힌트를 줄 뿐, **우선순위가 실행 순서를 보장하지 않음**
- 동기화 및 순차성이 중요한 작업은 반드시 **단일 스레드** 또는 **락 제어**로 구성 필요

---
  
## ✅ Thread 사용 시 주의사항

- 동시성 문제 → `synchronized`, `Lock`, `volatile` 등 적절한 동기화 필수
- Context Switching 비용 고려
- 데드락, 라이브락, 우선순위 역전 현상 예방 필요
- ThreadPoolExecutor 또는 Spring `@Async` 적극 활용

---
  
# 연결문서
- [Thread Dump](../../servercommon/servercommon-Thread-Dump)
