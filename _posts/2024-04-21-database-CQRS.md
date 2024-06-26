---
title : "CQRS"
excerpt : "CQRS"
toc : true
toc_sticky : true
toc_label : "CQRS"
categories:
- Database
tags:
- [Database]
last_modified_at: 2024-04-21T08:00:00-10:00:00
---
  
---
  
> **CQRS란?**  
>
> Command and Query Responsibility Segregation 의 약어로 데이터 저장소로부터 읽기와 업데이트 작업을 분리하는 소프트웨어 아키텍처 패턴을 뜻한다. 
{: .notice--info}  

 **전통적인 소프트웨어 아키텍처**는 **읽기와 쓰기 작업에서 사용되는 데이터 표현이 서로 일치하지 않는 경우가 많다**. 또한 동일한 데이터 set에 대한 **병렬 작업이 수행되면, 경합이 발생**할 우려가 있고 **정보조회에 복잡한 쿼리가 필요**하다. 이 때문에 **성능이 저하**되며, 하나의 모델이 읽기과 쓰기를 모두 수행할 경우 **보안 관리에 어려움**이 있을 수 있다.

 이러한 전통적인 소프트웨어 아키텍처의 단점들은 읽기와 쓰기를 분리하여 보완할 수 있다. **CQRS 패턴**을 사용하면

 첫째, 읽기와 쓰기 작업을 분리하여 **각 작업을 최적화** 할 수 있다. 예를 들어 읽기 작업에 대해 복잡한 조인 없이 단순한 조회만 수행할 수 있도록 데이터베이스를 최적화 할 수 있다.

 둘째, 읽기와 쓰기 작업을 **각각 독립적으로 확장**할 수 있다. 읽기 작업이 많다면 읽기 데이터베이스를 복제하여 부하를 분산시킬 수 있다.

 셋째, 읽기와 쓰기 작업에 대해 **별도의 접근 제어 정책을 적용**할 수 있다.

 넷째, 비즈니스 로직이 복잡해질수록 다른 패턴에 비해 **가독성과 유지보수성이 향상**된다. 또한 명령과 쿼리를 분리하기 때문에 **책임을 명확이 할 수 있다**.
  
 반면에 [ORM](../../servercommon/servercommon-ORM) 툴을 통해 **DB 스키마에서 자동 생성이 불가능** 하고, 메시지 실패나 중복메시지에 대한 **예외처리가 필요하다**는 단점이 있다. 또한 읽기, 쓰기 저장소가 분리된다면, **지연으로 인한 데이터 불일치 현상**이 발생할 수 있다.

---
  
# 연결문서
- [ORM](../../servercommon/servercommon-ORM)