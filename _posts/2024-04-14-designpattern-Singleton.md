---
title : "Singleton"
excerpt : "Singleton"
toc : true
toc_sticky : true
toc_label : "Singleton"
categories:
- DesignPattern
tags:
- [DesignPattern]
last_modified_at: 2024-04-14T08:00:00-10:00:00
---
  
---
  
## 📌 Singleton 패턴이란?

> **info**
>
> Singleton 패턴은 **프로그램 내에서 하나의 인스턴스만 존재하도록 보장**하는 디자인 패턴이다.  
> 주로 설정 객체나 공통 유틸리티 등에 사용되며, **전역 접근 지점(Global Access Point)**을 제공한다. 
{: .notice--info}  

---
  
## ✅ Singleton의 장점

- 메모리 낭비 방지 (하나의 객체만 생성)
- 전역 상태 공유 (모든 호출 지점에서 동일 객체 사용)
- 객체 생성 비용이 큰 경우 재사용 가능

---
  
## ✅ Singleton의 단점

- **멀티스레드 환경에서 동기화 필요**
- **단위 테스트 어려움** (상태가 공유되기 때문)
- **클래스 간 결합도 증가 가능성**

---
  
## ✅ Singleton 구현 예시 (Java - Double Checked Locking 방식)
  
```java
public class DoubleCheckedLockingSingleton {
    private static volatile DoubleCheckedLockingSingleton instance;

    private DoubleCheckedLockingSingleton() {
        // private constructor to prevent instantiation
    }

    public static DoubleCheckedLockingSingleton getInstance() {
        if (instance ** null) {
            synchronized (DoubleCheckedLockingSingleton.class) {
                if (instance ** null) {
                    instance = new DoubleCheckedLockingSingleton();
                }
            }
        }
        return instance;
    }
}
```

> **tip**
>
> `volatile` 키워드와 `synchronized` 블록을 통해 **동시성 문제를 해결**하고 **지연 초기화(lazy initialization)**를 구현함. 
{: .notice--info}  

---
  
## ✅ Singleton 패턴 사용 사례

- 설정 파일 관리 객체
- 로그 관리자 (Logger)
- DB 연결 풀 (Connection Pool)
- 공통 연산 유틸 클래스

---
  
## ✅ 기타 Singleton 구현 방법
  
### 🔹 정적 초기화 방식
  
```java
public class StaticSingleton {
    private static final StaticSingleton instance = new StaticSingleton();
    private StaticSingleton() {}
    public static StaticSingleton getInstance() {
        return instance;
    }
}
```

- 초기화가 빠르고 간단하지만 **lazy loading 불가능**

---
  
### 🔹 Enum 방식 (가장 권장됨 - Effective Java)
  
```java
public enum EnumSingleton {
    INSTANCE;
}
```

- **직렬화/역직렬화에도 안전**
- Java에서 가장 간단하고 안전한 Singleton 구현

---
  
# 연결문서
- [Thread](../../servercommon/servercommon-Thread)
