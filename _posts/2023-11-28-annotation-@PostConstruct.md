---
title : "@PostConstruct"
excerpt : "@PostConstruct"
toc : true
toc_sticky : true
toc_label : "@PostConstruct"
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
- 빈이 생성되고 의존 관계 주입이 완료된 후 실행되는 **초기화 콜백을 적용**할 수 있음

## 특징
- @PostConstruct 어노테이션이 적용된 메서드는 WAS가 기동될 때, 실행 된다.
- 초기화 작업이 필요한 메서드 위에 선언
- static 메서드는 될 수 없음
- 다른 리소스에서 호출하지 않아도 자동 실행
- 다른 프레임워크에서도 사용 가능

## 사용법

``` java
@PostConstruct  
public void init() {  
   Thread thread = new Thread(this);  
   thread.start();  
}
```

---

# 연결문서
- [SpringBean LifeCycle](../../spring/spring-SpringBean-LifeCycle)
- [@PreDestory](../../annotation/annotation-@PreDestory)