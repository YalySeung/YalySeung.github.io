---
title : "Critical Section"
excerpt : "Critical Section"
toc : true
toc_sticky : true
toc_label : "Critical Section"
categories:
- DevelopCommon
tags:
- [DevelopCommon]
last_modified_at: 2023-12-08T08:00:00-10:00:00
---

# 날짜 : 2023-12-08 11:10

# 태그 : #DevelopCommon
---

# 내용

## 정의
> Critical Section이란?

  공유 자원에 접근하는 코드 영역

## Critical Section 문제
- 하나의 프로세스 안에는 1개 이상의 쓰레드들이 존재
- 각 쓰레드들은 각자의 Stack과 Register만 독립적으로 가지고 있음
- 이외의 나머지 자원들은 공유함으로써 문제가 발생

# Thread 동기화 방법

## User Mode Synchronization
- 동기화 과정에서 Kernel의 자원을 이용하지 않음 -> 성능상의 이점

### Critical Section
- 코드 영역 자체를 보호할 때 사용
- 한 프로세스 내의 Thread들 간의 동기화 가능

### Interlock Synchronization
- 전역변수 하나의 접근에 동기화

## Kernel Mode Synchronization
- 동기화 과정에서 Kernel의 자원을 이용 -> Kernel Mode 로 전환되며 성능저하 발생
- User Mode에서 제공하지 못하는 기능들 제공

### Mutex
- Mutual exclusion(상호배제)의 약자
- Kernel 오브젝트인 Mutex를 이용한 동기화 기법
- <span style="color:red">Lock을 실행한 Thread가 Critical Section에서 나갈 때만 utex 해제</span>
- 여러 프로세스의 Thread 사이에서 동기화 가능
- 한개의 Critical Section만 동기화 가능(Mutex는 한개의 Critical Setion을 소유한다 or 책임진다)
- 일정 시간을 주기로 계속 Acquire를 반복 호출하여 Critical Section에 접근 가능한지 여부를 확인("Busy Waiting", "spinlock")
- CPU 사이클을 계속해서 낭비하는 단점

### Semaphore
- 받아들일 수 있는 Thread 또는 Process의 수를 semaphore는라고 부름
- 지정된 수 만큼의 Thread가 동시에 실행되도록 동기화
- 다중프로세스 동기화 기법
- <span style="color:red">Lock을 실행하지 않은 다른 Thread에서도 Signal을 보내 ock을 해제할 수 있음</span>
- wait와 signal이라는 개의 atomic operation 사용
- Binary Semaphore(count = 1), Counting Semaphore(count > 1)가 존재
- 하나의 Critical Section 에 2개 이상의 Thread 또는 Process 진입 가능
- Thread 또는 Process가 Lock을 획득하면 semaphore는 감소
- Thread 또는 Process가 Lock을 반환하면 semaphore는 증가

---

# 연결문서
- [Thread](../../ServerCommon/ServerCommon-Thread)