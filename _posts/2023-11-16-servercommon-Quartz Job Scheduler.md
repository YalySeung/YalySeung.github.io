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
  
## 정의
> **info**
>
>Java로 개발된 Job Scheduling library 
{: .notice--info}  
  
## 장점
- DB 기반으로 스케쥴러 간 Clustering 제공
- Fail-over와 Random 방식의 로드 분산 처리 지원
- In-memory Job Scheduler 제공
- 여러 기본 plugin 제공
  
## 단점
- Clustering 기능을 제공하지만, 단순한 random 방식이라 완벽한 로드 분산은 어렵다
- Admin UI 미제공
- 스케쥴링 실행에 대한 History 기록 X
- Fixed Delay 타입 미지원
  
## Quartz Workflow
  
![image](../../assets/images/QuartzWorkflow.png)
  
## Quartz Classes
  
### Job
- 실제 실행 되어야 하는 작업
- Job Interface의 execute 메서드를 구현 하여 실제 로직을 적용
  
```java
public class CustomJob implements Job {    
   @Override  
   public void execute(JobExecutionContext context) throws JobExecutionException {  
      //...수행할 로직
   }  
}
```  
- JobExecutionContext는 Scheduler, Trigger, JobDetail 등을 포함하여 Job 인스턴스에 대한 정보를 제공하는 객체
  
### JobDataMap
- Job 인스턴스가 실행할 때 사용할 기타 정보를 담을 객체
- JobDetail 생성 시점에 JobDataMap도 함께 생성
- JobExecutionContext.getJobDetail() 로 가져와서 사용
  
```java
//set
JobDetailImpl.setJobDataMap(new JobDataMap())

   public void execute(JobExecutionContext context) throws JobExecutionException {  
      //...수행할 로직
	//get
	JobDataMap jobDataMap = context.getJobDetail().getJobDataMap()
   }  
```
  
### JobDetail
- Job을 실행시키기 위한 정보를 담은 객체
- Name, Group, JobDataMap 속성 등
- Trigger 가 Job 을 수행할 때 이 정보를 기반으로 스케쥴링
  
### Trigger
- Job을 실행시킬 스케쥴링 조건
  
#### SimpleTrigger
- 특정 시간에 Job을 수행시키는 trigger
- 반복횟수, 실행 간격 지정
  
#### CronTrigger
- [Cron Expression](../../expression/expression-Cron-Expression)으로 trigger를 정의하는 방식
  
### Misfire Instruction
- Scheduler가 Misfire된 Trigger에 대해서 어떻게 처리할지에 대한 다양한 policy 지원
  
#### Misfire
-  Job이 실행되어야 하는 시간, fire time을 지키지 못한 실행 불발
- Scheduler가 종료되거나 쓰레드 풀에 사용가능한 쓰레드가 없을 경우 발생
  
### Listener
- Schedule의 이벤트를 받을 수 있도록 Quartz에서 제공하는 인터페이스
  
#### JobListener
- Job 실행 전후로 이벤트 수신
  
```java
public class GlobalJobDetailListener implements JobListener {  
    private static final Logger logger = LoggerFactory.getLogger(GlobalJobDetailListener.class);  
  
    private static final String LISTENER_NAME = "globalJobDetailListener";  
  
    @Override  
    public String getName() {  
        return LISTENER_NAME;  
    }  
  
    @Override  
    public void jobToBeExecuted(JobExecutionContext context) {  
        logger.info("[jobToBeExecuted] jobKey : {}, triggerKey : {}", context.getJobDetail().getKey(),  
                context.getTrigger().getKey());  
    }  
  
    @Override  
    public void jobExecutionVetoed(JobExecutionContext context) {  
  
    }  
    @Override  
    public void jobWasExecuted(JobExecutionContext context, JobExecutionException jobException) {  
        logger.info("[jobWasExecuted] jobKey : {}, triggerKey : {}", context.getJobDetail().getKey(),  
                context.getTrigger().getKey());  
    }  
}
```
  
#### TriggerListener
- Trigger가 발생, 완료하거나 Misfire 될 경우 이벤트 수신
  
```java
public class QuartzTriggerListener implements  TriggerListener  {  
   @Override  
   public String getName() {  
      return "TestTriggerListener";  
   }  
  
   @Override  
   public void triggerFired(Trigger trigger, JobExecutionContext context) {  
         String triggerName = context.getJobDetail().getKey().toString();  
          // System.out.println("triggerFired");  
           System.out.println("[TriggerListener] trigger (" + triggerName + ") is fired");  
   }  
  
   @Override  
   public boolean vetoJobExecution(Trigger trigger, JobExecutionContext context) {  
       boolean veto = false;  
       //System.out.println("Veto Job Excecution trigger: " + veto);  
        return veto;  
   }  
  
   @Override  
   public void triggerMisfired(Trigger trigger) {  
       System.out.println("[TriggerListener] " +getName() + " trigger (" + trigger.getKey() + ") misfired at " + trigger.getStartTime());  
   }  
  
   @Override  
   public void triggerComplete(Trigger trigger, JobExecutionContext context,  
         CompletedExecutionInstruction triggerInstructionCode) {  
       System.out.println("[TriggerListener] "+getName() + " trigger (" + trigger.getKey() + ") completed at " + trigger.getStartTime());  
   }       
}
```
  
### JobStore
- Job과 Trigger 정보를 설정
  
#### RAMJobStore
- 기본값으로 메모리에 스케쥴 정보를 저장
- 메모리에 저장하기 때문에 성능 좋음
- 시스템 문제 발생시 스케쥴 데이터 유지 불가
  
#### JDBC JobStore
- 스케쥴 정보를 DB에 저장
- 시스템 문제 발생시에도 스케쥴 정보 유지
  
#### etc JobStore
- Quartz JobStore를 확장하여 다른 저장소에도 저장 가능

---
  
# 연결문서