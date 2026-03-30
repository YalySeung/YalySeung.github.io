---
title : "Executor"
excerpt : "Executor"
toc : true
toc_sticky : true
toc_label : "Executor"
categories:
- Spring
tags:
- [Spring]
last_modified_at: 2026-03-27T08:00:00-10:00:00
---
  
---
  
## 📌 Executor란?

> **info**
>
> Executor는 **비동기 작업을 처리하기 위한 스레드 풀 관리 컴포넌트**이다. 
{: .notice--info}  

 작업을 별도의 스레드에서 실행하여 **병렬 처리 및 성능 개선**을 가능하게 한다.

---
  
## 📌 왜 Executor를 사용하는가

- 비동기 처리 (@Async)
- 병렬 API 호출
- IO 작업 병목 해소
- 대량 요청 처리

 **단일 스레드 처리 구조를 병렬 구조로 개선**하기 위해 사용한다.
 
---
  
## 📌 기본 구조

 Executor는 다음 3가지 요소로 구성된다.

| 요소 | 설명 |
|-----|-----|
| Thread Pool | 스레드 집합 |
| Queue | 대기 작업 저장 |
| Worker Thread | 실제 작업 실행 |

---
  
## 📌 주요 설정 값

| 옵션 | 설명 |
|-----|-----|
| corePoolSize | 기본 유지 스레드 수 |
| maxPoolSize | 최대 스레드 수 |
| queueCapacity | 작업 대기 큐 크기 |
| keepAliveSeconds | 유휴 스레드 유지 시간 |

---
  
## 📌 기본 Executor 설정 (Spring Boot)
  
```java
@Bean
public ThreadPoolTaskExecutor taskExecutor() {
    ThreadPoolTaskExecutor executor = new ThreadPoolTaskExecutor();
    executor.setCorePoolSize(10);
    executor.setMaxPoolSize(20);
    executor.setQueueCapacity(100);
    executor.setThreadNamePrefix("EXEC-");
    executor.initialize();
    return executor;
}
```

---
  
## 📌 CompletableFuture.supplyAsync

> **info**
>
> `supplyAsync`는 **비동기 작업을 실행하고 결과를 반환**하는 메서드이다. 
{: .notice--info}  
  
```java
CompletableFuture<String> future =
    CompletableFuture.supplyAsync(() -> "result", taskExecutor);
```

---
  
## 📌 병렬 처리 + 결과 취합
  
```java
List<CompletableFuture<String>> futures = list.stream()
    .map(item -> CompletableFuture.supplyAsync(() -> process(item), taskExecutor))
    .toList();

// 모든 작업 완료 대기
CompletableFuture.allOf(futures.toArray(new CompletableFuture[0])).join();

// 결과 취합
List<String> results = futures.stream()
    .map(CompletableFuture::join)
    .toList();
```

- `allOf` → 전체 완료 대기
- `join()` → 결과 수집

 **병렬 처리 후 결과를 하나의 리스트로 취합 가능**

---
  
## 📌 Semaphore란?

> **info**
>
> Semaphore는 **동시에 실행 가능한 작업 수를 제한**하는 동시성 제어 도구이다. 
{: .notice--info}  

---
  
## 📌 Semaphore + Executor
  
```java
Semaphore semaphore = new Semaphore(10);

CompletableFuture<String> future =
    CompletableFuture.supplyAsync(() -> {
        try {
            semaphore.acquire();
            return callExternalApi();
        } catch (InterruptedException e) {
            Thread.currentThread().interrupt();
            return null;
        } finally {
            semaphore.release();
        }
    }, taskExecutor);
```

---
  
## 📌 전체 흐름 정리
  
```java
Semaphore semaphore = new Semaphore(10);

List<CompletableFuture<String>> futures = list.stream()
    .map(item -> CompletableFuture.supplyAsync(() -> {
        try {
            semaphore.acquire();
            return process(item);
        } catch (InterruptedException e) {
            Thread.currentThread().interrupt();
            return null;
        } finally {
            semaphore.release();
        }
    }, taskExecutor))
    .toList();

// 전체 완료 대기
CompletableFuture.allOf(futures.toArray(new CompletableFuture[0])).join();

// 결과 취합
List<String> results = futures.stream()
    .map(CompletableFuture::join)
    .toList();
```

---
  
## 📌 핵심 정리

| 요소 | 역할 |
|-----|-----|
| Executor | 스레드 풀 관리 |
| supplyAsync | 비동기 실행 |
| Semaphore | 동시 실행 제한 |
| allOf | 전체 완료 대기 |
| join | 결과 취합 |

---
  
## 📌 Executor 분리 전략

> **tip**
>
> 작업 성격에 따라 Executor를 분리하는 것이 중요하다.
> API Response로 FileStream을 사용한다면 분리하는 것을 권장한다. 
{: .notice--info}  
  
### IO 작업용 Executor
  
```java
executor.setCorePoolSize(20);
executor.setMaxPoolSize(50);
executor.setQueueCapacity(200);
```
  
### CPU 작업용 Executor
  
```java
executor.setCorePoolSize(4);
executor.setMaxPoolSize(8);
executor.setQueueCapacity(50);
```

---
  
## 📌 결론

 Executor + CompletableFuture + Semaphore를 조합하면

- **비동기 처리**
- **병렬 처리**
- **동시성 제어**
- **결과 취합**

을 모두 구현할 수 있다.

---
  
# 연결 문서