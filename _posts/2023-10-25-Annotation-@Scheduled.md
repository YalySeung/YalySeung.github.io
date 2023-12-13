---
title : "@Scheduled"
excerpt : "@Scheduled"
toc : true
toc_sticky : true
toc_label : "@Scheduled"
categories:
- Annotation
tags:
- [Spring, Annotation]
last_modified_at: 2023-10-25T08:00:00-10:00:00
---

# 날짜 : 2023-10-25 11:47

# 태그 : #Spring #Annotation 
---

# 내용

## Artifact
- **spring-context**

## 역할
- 일정한 시간 간격 또는 특정 시간에 함수가 실행 되도록 할수 있다.

## 사용법
- Configuration에 @EnableScheduling Annotation을 적용

```java
@EnableWebMvc  
@EnableScheduling  
@ComponentScan(basePackages = "org.test")  
public class WebMvcTestConfiguration implements WebMvcConfigurer {  
    @Override  
    public void configureViewResolvers(ViewResolverRegistry registry) {  
        InternalResourceViewResolver resolver = new InternalResourceViewResolver();  
        resolver.setPrefix("/WEB-INF/");  
        resolver.setSuffix(".jsp");  
        registry.viewResolver(resolver);  
    }  
}
```

- Schedule이 필요한 함수에 @Scheduled Annotation 적용

```java 
@Component  
public class ScheduleSample {  
    @Scheduled(cron ="0 0/1 * * * ?")  
    public void doEveryOneMinutes(){  
        System.out.println(LocalTime.now() + " : doEveryOneMinutes");  
    }  
}
```

- 결과
  
![image](../../assets/images/ScheduleResult.png)

### Schedule Option

#### cron
- cron 표현식을 사용
- ex)

```java 
@Scheduled(cron ="0 0/1 * * * ?")  
public void doEveryOneMinutes(){  
	System.out.println(LocalTime.now() + " : doEveryOneMinutes");  
}  
```

```java
@Scheduled(cron = "#{@getCronForDeleteOldTaskQueue}")  
public void deleteOldTaskQueue() {  
    Integer[] values = getBatchExecutingInfoValues(BatchJobTypeCode.BATCH_DELETE_OLD_TASK_QUEUE, new Integer[] {30});  
    taskQueueWebService.deleteOldTaskQueue(values[0]);  
}
```

#### fixedDelay
- 해당 메소드가 종료된 이후부터 그다음 메소드 실행시간까지의 주기
- 단위 : ms

```java
@Scheduled(fixedDelay = 3000) 
private void scheduleTest() { logger.error("hello"); }
```

#### fixedDelayString
- properties로 부터 실행 주기 입력

#### fixedRate
- 해당 메소드가 실행된 직후부터의 주기
- 단위 : ms

#### fixedRateString
- properties로 부터 실행 주기 입력

```java
@Scheduled(fixedRateString = "${myscheduler.period}") 
private void scheduleTest() { logger.error("hello"); }
```

#### initialDelay
- 스케줄러에서 메서드가 등록되자마자 수행하는 것이 아닌 초기 지연시간을 설정

```java
@Scheduled(initialDelay = 3000) 
private void scheduleTest() { logger.error("hello"); }
```

#### initialDelayString
- properties로 부터 실행 주기 입력

---

# 연결문서
- [SpringMVC](../../spring/Spring-SpringMVC)
- [SpringMVC 구현](../../spring/Spring-SpringMVC-구현)
- [Cron Expression](../../expression/Expression-Cron-Expression)