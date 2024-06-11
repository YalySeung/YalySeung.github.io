---
title : "volatile"
excerpt : "volatile"
toc : true
toc_sticky : true
toc_label : "volatile"
categories:
- java
tags:
- [Java]
last_modified_at: 2024-01-31T08:00:00-10:00:00
---
  
---
  
## 정의
> **Volatile 이란?**  
>
> java 변수를 Main Memory에 저장하는 키워드이다. 
{: .notice--info}  

 volatile 을 왜 사용해야 하는지 알아보자. 
  
![image](../../assets/images/CPUCache.png)
 
 위 이미지에서 볼 수 있듯 **Multi Thread** 애플리케이션에서의 **non-volatile 변수는 CPU 캐시를 사용**한다. 그래서 JVM이 메인 메모리와 CPU cache중 어떤 곳에서 데이터를 가져올지 알 수 없으며, **데이터 동기화에도 문제**가 생긴다. volatile 키워드는 이런 문제를 **보완** 할 수 있다.

 volatile은 변수값 Read/Write 시점에 CPU 캐시된 데이터가 아닌 **Main Memory의 데이터를 Read/Write**한다. 하지만 cache를 사용하지 않는다는 것 만으로 원자성 보장 할 수 없다. **한 쓰레드에서만 쓰고, 여러 쓰레드에서 Read 할 때**는 문제가 없지만 여러 쓰레드에서 Write를 해야할 경우 synchronized 블록이나 Atomic Class와 함께 사용하여 원자성을 확보할 수 있다.

> **caution**
>
> volatile 키워드가 항상 원자성을 보장해주는 것은 아니다.  여러 쓰레드에서 동시에 Main Memory에 접근하여 Read/Write 를 수행한다면, 값이 변경되는 사이에 Read 될 수 있기 때문이다. 
{: .notice--info}  

 volatile 키워드를 사용하는 방법은 간단하다.
  
```java
public volatile int count = 0;
```

---
  
# 연결문서
