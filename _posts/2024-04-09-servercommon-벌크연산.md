---
title : "벌크연산"
excerpt : "벌크연산"
toc : true
toc_sticky : true
toc_label : "벌크연산"
categories:
- ServerCommon
tags:
- [ServerCommon, 미완료]
last_modified_at: 2024-04-09T08:00:00-10:00:00
---
  
---
  
> **벌크 연산이란?**  
>
> Database나 프로그래밍에서 다수의 데이터를 한번에 처리하는 작업을 말한다. 
{: .notice--info}  

 일반적으로 데이터베이스에서 벌크 연산을 사용하는 이유는 **성능을 최적화**하고, 트랜잭션 **오버헤드를 줄이기 위함**이다. 하지만 주의해야 할 사항이 있다. 한번에 많은 데이터를 다루는 만큼 **메모리 사용량을 고려**해야 하며, **너무 많은 데이터를 처리하면 Database 성능에 부정적인 영향**을 미칠 수 있다.

 벌크 연산의 예시를 몇 가지 살펴보자
  
```sql
INSERT INTO employees (name, position, salary) 
VALUES 
('John Doe', 'Developer', 60000), 
('Jane Smith', 'Manager', 75000), 
('Alice Johnson', 'Analyst', 50000);
```
 이 sql은 벌크 삽입의 예시이다
  
```sql
UPDATE employees 
SET salary = salary * 1.10 
WHERE position = 'Developer';
```
 이 sql은 벌크 수정 연산의 예시이다.

---
  
# 연결문서
