---
title : "CommonDB"
excerpt : "CommonDB"
toc : true
toc_sticky : true
toc_label : "CommonDB"
categories:
- Database
tags:
- [Database, CommonDB]
last_modified_at: 2023-10-13T08:00:00-10:00:00
---
  
---
  
 이 글에서는 Database에서 공통적으로 사용하는 키워드에 대해서 살펴보겠다.

 먼저 **UNION** 키워드는 두개의 테이블을 행 단위로 연결하는 역할을 한다. 그 과정에서 **중복되는 Row는 결과에 하나만 포함시키고 나머지는 제거**한다. 반면에 **UNION ALL**은 **중복된 Row 를 제거하지 않고** 두개의 테이블을 행 단위로 연결시킨다. 중복에 대한 처리가 없기 때문에 **속도면에서 UNION보다 빠르다**. UNION과 UNION ALL 키워드를 사용하기 위해서는 각 대상 테이블 **SELECT 절의 컬럼 개수가 같아야한다**.
  
```sql
SELECT order_id, order_date, total_amount FROM orders 
UNION 
SELECT invoice_id, invoice_date, invoice_total_amount FROM invoices;
```

---
  
# 연결문서
