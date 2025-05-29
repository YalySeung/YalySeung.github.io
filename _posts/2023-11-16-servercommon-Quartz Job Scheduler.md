---
title : "Quartz Job Scheduler"
excerpt : "Quartz Job Scheduler"
toc : true
toc_sticky : true
toc_label : "Quartz Job Scheduler"
categories:
- ServerCommon
tags:
- [ServerCommon]
last_modified_at: 2023-11-16T08:00:00-10:00:00
---
  
---
  
## 📌 Quartz란?

> **info**
>
> Quartz는 Java 기반의 **스케줄링 프레임워크**로, 정기적인 작업 실행을 위한 Job Scheduler이다.  
> 다양한 트리거 조건, 클러스터링, 영속성 저장소 지원 등 **유연하고 확장 가능한 스케줄링 시스템**을 제공한다. 
{: .notice--info}  

---
  
## ✅ Quartz 주요 장점

- DB 기반 클러스터링 구성 가능
- In-memory 기반 경량 스케줄링도 가능
- 다양한 기본 Plugin 지원
- Fail-over, Random 로드 분산 제공
- 다양한 Trigger 전략(Cron, Simple 등) 및 Misfire 정책 존재

---
  
## ❌ Quartz 단점

- 로드밸런싱은 단순 Random 수준
- Admin UI 부재 → 직접 구현 필요
- 실행 이력 저장 기능 없음 (추가 구현 필요)
- Fixed Delay 지원 X → Spring Scheduler가 더 적합한 경우 있음

---
  
## ✅ Quartz 핵심 구성요소
  
### 1. Job
- 실행 로직이 포함된 클래스
- `Job` 인터페이스를 구현하여 `execute` 메서드 정의
  
```java
public class CustomJob implements Job {
   public void execute(JobExecutionContext context) {
      // 작업 로직
   }
}
```
  
### 2. JobDetail
- Job 인스턴스 정보 (이름, 그룹, JobDataMap 포함)
- Trigger가 이 JobDetail을 기준으로 작업 실행

---
  
### 3. JobDataMap
- 실행 시 필요한 데이터 전달용
- `JobExecutionContext`에서 `getJobDetail().getJobDataMap()`으로 접근

---
  
### 4. Trigger

| 종류 | 설명 |
|------|------|
| `SimpleTrigger` | 고정 간격 반복 작업 |
| `CronTrigger` | `Cron Expression` 기반 정교한 시간 조건 지정 가능 |
  
```java
Trigger trigger = TriggerBuilder.newTrigger()
    .withSchedule(CronScheduleBuilder.cronSchedule("0 0 12 * * ?"))
    .build();
```

---
  
### 5. Misfire 정책

| 개념 | 설명 |
|------|------|
| Misfire | Job이 지정된 시간에 실행되지 못한 상황 |
| Instruction | Skip, Now 실행, 재시도 등 정책 설정 가능 |

---
  
### 6. Listener

| 리스너 | 설명 |
|--------|------|
| `JobListener` | Job 실행 전/후 이벤트 감지 |
| `TriggerListener` | Trigger 실행, 완료, Misfire 이벤트 감지 |
  
```java
public class GlobalJobDetailListener implements JobListener {
   public void jobToBeExecuted(JobExecutionContext context) {
      log.info("Job 실행 전: {}", context.getJobDetail().getKey());
   }
   public void jobWasExecuted(JobExecutionContext context, JobExecutionException ex) {
      log.info("Job 실행 후: {}", context.getJobDetail().getKey());
   }
}
```

---
  
### 7. JobStore

| 종류 | 설명 |
|------|------|
| `RAMJobStore` | 메모리 기반, 성능 좋으나 휘발성 |
| `JDBCJobStore` | DB 저장소 기반, 스케줄 정보 유지 |
| Custom | 기타 확장 구현 가능 (ex: Mongo, Redis 등)

---
  
## 🔄 Quartz 동작 순서
  
![image](../../assets/images/QuartzWorkflow.png)

1. Scheduler 인스턴스 생성
2. JobDetail, Trigger 생성
3. Scheduler에 Job + Trigger 등록
4. Scheduler 시작
5. Trigger 조건에 맞춰 Job 실행

---
  
# 연결문서
- [Cron Expression](../../expression/expression-Cron-Expression)
- [JDBC](../../servercommon/servercommon-JDBC)
