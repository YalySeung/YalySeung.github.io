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

# 날짜 : 2023-10-13 15:47

# 태그 : #Database #CommonDB
---

# 내용

### UNION
- 두개의 테이블을 행 단위로 연결하는 키워드

#### 특징
- 중복 로우 제거
- 열 수와 데이터 유형이 일치해야함
- 중복값을 포함하려면 UNION ALL 사용
- 첫번째 SELECT 문이 열의 수와 데이터 유형을 정의함

#### 예시

```sql
SELECT order_id, order_date, total_amount FROM orders 
UNION 
SELECT invoice_id, invoice_date, invoice_total_amount FROM invoices;
```

---

# 연결문서
