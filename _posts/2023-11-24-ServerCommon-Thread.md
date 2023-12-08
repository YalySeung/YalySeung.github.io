---
title : "Thread"
excerpt : "Thread"
toc : true
toc_sticky : true
toc_label : "Thread"
categories:
- ServerCommon
tags:
- [ServerCommon, java]
last_modified_at: 2023-11-24T08:00:00-10:00:00
---

# 날짜 : 2023-11-24 14:38

# 태그 : #ServerCommon #java
---

# 내용

## 정의
> Thread란
>프로세스 안에서 실질적으로 작업을 실행하는 흐름의 단위

## 종류

### Non-Daemon Thread
- 끝까지 실행 됨
- JVM은 사용자 스레드가 작업을 완료할 때까지 대기
- 모든 사용자 스레드가 종료될 때까지 종료되지 않음
- ex) Main Thread

### Daemon Thread
- Main Thread를 돕는 보조역할을 수행하는 Thread
- Main Thread가 종료되면 함께 종료됨
- ex) GC

## LifeCycle
![image](./../../assets/images/../../assets/Images/JavaThreadLifeCycle.png)

## State

| 상태       | 설명                                                                        |
| ---------- | --------------------------------------------------------------------------- |
| NEW        | 처음 스레드가 생성된 상태                                                   |
| RUNNABLE   | 실행 대기 상태, start가 호출된 상태                                         |
| RUNNING    | 실행중인 상태,        run이 호출된 상태                                     |
| WAITING    | 일시 정지 상태, 다른 스레드가 통지할 때까지 기다리는 상태                   |
| TIMED_WAIT | 일시 정지 상태, 주어진 시간동안 기다리고 있는 상태                          |
| BLOCKED    | 일시 정지 상태, 사용하려고 하는 객체의 Lock이 풀릴때까지 기다리고 있는 상태 |
| TERMINATED | 종료 상태, 실행을 마친 상태                                                 |

## Priority

```java
/* The minimum priority that a thread can have.  */ 
public final static int MIN_PRIORITY = 1;  
  
/* The default priority that is assigned to a thread.  */ 
public final static int NORM_PRIORITY = 5;  
  
/* The maximum priority that a thread can have.  */ 
public final static int MAX_PRIORITY = 10;
```

- Thread 호출 순서에 영향을 주지만 절대적이지는 않다.
- 실행 순서에 따라 영향이 있는 로직은 한 쓰레드로 처리하는게 바람직 하다.

---

# 연결문서
- [Thread Dump](../../ServerCommon/ServerCommon-Thread-Dump)