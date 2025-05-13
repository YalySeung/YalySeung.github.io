---
title : "명시적 Rollback"
excerpt : "명시적 Rollback"
toc : true
toc_sticky : true
toc_label : "명시적 Rollback"
categories:
- Spring
tags:
- [Spring]
last_modified_at: 2025-03-27T08:00:00-10:00:00
---
  
---
  
> **명시적 Rollback이란?**  
>
> Spring에서 트랜잭션 중 특정 조건이 충족되었을 때 **개발자가 명시적으로 롤백 처리를 수행하도록 설정하는 방법**이다. 
{: .notice--info}  

 Spring의 기본 트랜잭션 관리는 RuntimeException 발생 시 자동으로 롤백되지만, 경우에 따라 개발자가 명시적으로 롤백을 수행할 필요가 있다. 이때 사용하는 메서드가 바로 아래와 같다.

---
  
## 📌 명시적 롤백 설정 방법
  
### 🎯 `TransactionAspectSupport`

Spring AOP의 트랜잭션 관리 내에서 현재 트랜잭션 상태를 가져와 강제로 롤백을 명령할 수 있다.
  
```java
TransactionAspectSupport.currentTransactionStatus().setRollbackOnly();
```

이 메서드는 현재 진행 중인 트랜잭션을 즉시 커밋되지 않고 롤백 상태로 표시한다.

---
  
## 📌 사용 예시
  
### 🎯 비즈니스 로직 내에서 조건에 따른 명시적 롤백
  
```java
@Service
@Transactional
public class OrderService {

    public void placeOrder(Order order) {
        try {
            // 주문 처리 로직
            orderRepository.save(order);

            if(order.getAmount() > 10000){
                throw new IllegalStateException("금액 초과");
            }

        } catch(Exception e) {
            // 조건 충족 시 명시적으로 롤백
            TransactionAspectSupport.currentTransactionStatus().setRollbackOnly();
        }
    }
}
```

위 예제는 특정 조건에서 예외 발생과 함께 명시적 롤백을 설정하여 트랜잭션을 안전하게 종료한다.

---
  
## 📌 주의사항

- **트랜잭션 범위 내에서만 사용 가능**
- **롤백 설정 이후 트랜잭션을 다시 커밋할 수 없음**

---
  
## 📌 장점과 단점
  
### ✅ 장점
- **정교한 트랜잭션 제어 가능**
- **비즈니스 로직에서 명확한 롤백 조건 설정 가능**
  
### ❌ 단점
- **코드 내에서 명시적인 관리 필요**
- **과도한 사용은 로직의 복잡성 증가 가능성**

---
  
## 📌 연결 문서
- [AOP](../../spring/spring-AOP)
