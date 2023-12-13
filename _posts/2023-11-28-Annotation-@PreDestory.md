---
title : "@PreDestory"
excerpt : "@PreDestory"
toc : true
toc_sticky : true
toc_label : "@PreDestory"
categories:
- Annotation
tags:
- [Spring, Annotation]
last_modified_at: 2023-11-28T08:00:00-10:00:00
---

# 날짜 : 2023-11-28 16:50

# 태그 : #Spring #Annotation
---

# 내용

## Artifact
- javax.annotation

## 역할
- Bean 소멸 전에 종료 전처리 Callback을 정의할 수 있음

## 특징
- bean 제거 직전 한번만 실행됨

## 사용법

``` java
@PreDestroy 
public void preDestroy() { 
	// 자원 반환 등 종료 처리 
	dbConnection.close(); 
}
```

---

# 연결문서
- [SpringBean LifeCycle](../../spring/Spring-SpringBean-LifeCycle)
- [@PostConstruct](../../annotation/Annotation-@PostConstruct)