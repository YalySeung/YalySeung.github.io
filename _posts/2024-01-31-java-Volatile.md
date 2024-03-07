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

# 날짜 : 2024-01-31 10:35

# 태그 :  #Java
---

# 내용

## 정의
> **Volatile 이란?**
>
> java 변수를 Main Memory에 저장하는 키워드
{: .notice--info}

## CPU cache
  
![image](../../assets/images/CPUCache.png)
- 멀티쓰레드 어플리케이션에서의 non-volatile 변수는 CPU 캐시를 사용함
- JVM이 상황에 따라 메인 메모리 또는 CPU cache중 어떤 곳에서 가져올지 보장하지 못함

## volatile의 기능
- 변수값 Read 시점에 CPU 캐시된 값이 아닌 Main Memory에서 Read
- 변수값 Wirte 시점에 Main Memory 값 갱신
- **한 쓰레드에서만 쓰고, 여러 쓰레드에서 Read 할 때 사용하는게 좋음**

## 사용법

```java
public volatile int count = 0;
```

> **caution**
>
> volatile 키워드가 항상 원자성을 보장해주는 것은 아니다.  여러 쓰레드에서 동시에 Main Memory에 접근하여 Read/Write 를 수행한다면, 값이 변경되는 사이에 Read 될 수 있기 때문이다.
{: .notice--danger}

> **tip**
>
> synchronized 블록이나 Atomic Class를 함께 사용하여 volatile 키워드를 보완 할 수 있다.
{: .notice--primary}

---

# 연결문서
