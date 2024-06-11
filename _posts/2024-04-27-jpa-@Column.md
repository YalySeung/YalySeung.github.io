---
title : "@Column"
excerpt : "@Column"
toc : true
toc_sticky : true
toc_label : "@Column"
categories:
- JPA
tags:
- [Spring, Annotation, 미완료, JPA]
last_modified_at: 2024-04-27T08:00:00-10:00:00
---
  
---
  
## Artifact
  
## 역할
  
## 사용법

| 속성               | 기능             |
| ---------------- | -------------- |
| name             | 컬럼명 설정         |
| length           | 데이터 Max 길이 설정  |
| nullable         | null값 가능 여부 설정 |
| precision        | 최대길이 설정        |
| scale            | 최소길이 설정        |
| columnDefinition | 컬럼 타입 지정       |
  
### 길이 범위 설정
  
```java
@Column(name = "AVG_CPU_USE_RATE", precision = 5, scale = 2)  
private Float averageCpuUseRate;
```
  
### Max 길이만 설정
  
```java
@Column(name = "TASK_ORD_DT", length = 6, nullable = false)  
private DateTime orderDateTime;
```
  
### Lob 타입 지정
  
```java
@Lob  
@Column(name = "QUE_DATA", columnDefinition = "CLOB")  
private String queueData;
```

---
  
# 연결문서
