---
title : "Singleton"
excerpt : "Singleton"
toc : true
toc_sticky : true
toc_label : "Singleton"
categories:
- DesignPattern
tags:
- [DesignPattern, 미완료]
last_modified_at: 2024-04-14T08:00:00-10:00:00
---
  
---
  
> **Singleton이란?**  
>
> 객체의 인스턴스가 오직 1개만 생성되는 패턴을 뜻한다. 
{: .notice--info}  
  
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

 **Singleton**은 최초 new 연산자로 생성된 객체를 계속해서 사용하기 때문에 **메모리 낭비를 방지** 할 수 있으며, 전역에서 접근이 가능한 static 메서드를 제공하여 **데이터 공유가 쉽다**. 
 반면 여러 thread에서 동시에 접근할 경우 **동시성 문제**가 발생할 수 있으므로 **synchronized 키워드와 함께 사용**하는 것이 좋다. 그리고 위 코드블럭에서 보다시피 일반 class보다 **코드 자체가 많이 필요**하고, 자원을 공유하고 있어 **테스트하기 어렵다**

 Singleton 패턴은 **설정파일**이나 연산을 도와주는 **Util Class**에 사용하는 것이 좋다.
  
---
  
# 연결문서
- [Thread](../../servercommon/servercommon-Thread)