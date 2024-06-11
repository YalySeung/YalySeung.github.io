---
title : "NoSQL"
excerpt : "NoSQL"
toc : true
toc_sticky : true
toc_label : "NoSQL"
categories:
- Database
tags:
- [Database]
last_modified_at: 2024-04-21T08:00:00-10:00:00
---
  
---
  
> **NoSQL이란>**  
>
> Non-Relational Operational DataBase 의 약어로, 주로 빅데이터, 분산 시스템 환경에서 대용량 데이터를 처리하는데 적합한 비관계형 Database를 뜻한다. 
{: .notice--info}  

 **NoSQL**은 데이터간 **Relation을 정의하지 않고 Key Value 데이터를 형태로 저장**하기 때문에 RDBMS에 비해 **대용량을 데이터를 관리**할 수 있다. 그리고 **분산형 구조**를 가지고 있어, 여러 곳의 서버에 데이터를 분산시킬 수 있기때문에 장애 대응이 용이하다. NoSQL의 **스키마는 유동적**이며, 데이터를 저장하는 **컬럼이 각기 다른 아름과 다른 데이터 타입을 가질 수 있다**는 특징이 있다

 NoSQL은 위와 같은 특징을 가지기 때문에 얻을 수 있는 장점이 있다.

 첫째, RDBMS에 비해 저렴한 비용으로 분산처리와 병렬처리가 가능하다.
 둘째, 비정형 데이터 구조 설계로 설계 비용이 감소한다.
 셋째, Big Data 처리에 효율적이다.
 넷째, 가변적인 구조로 데이터를 저장 가능하다.
 다섯째, 데이터 모델의 유연한 변화가 가능하다.

 반면, 단점도 있다.
 첫째, 데이터 업데이트 중 장애가 발생하면 데이터가 손실 될 수 있다.
 둘째, 많은 인덱스를 사용하려면 충분한 메모리를 필요로 한다.
 셋째, 데이터 일관성이 보장되지 않는다.

 지금부터는 NoSQL Database 모델을 종류별로 알아보겠다.
  
## Key-Value Database
 key와 value 쌍으로 데이터를 저장하는 Database이다. 이 Database 모델은 간단하고 효율적이다.

| 종류                          |
| --------------------------- |
| Redis                       |
| Oracle NoSQL DB, VoldeMorte |
  
## Wide-Column Database
 전통적인 Database와 같이 행과 열을 사용하지만, 각행이 서로 다른 구조를 가질 수 있어 대규모 데이터 처리와 높은 읽기/쓰기 성능을 요구하는 환경에서 유리하다.

| 종류             |
| -------------- |
| Hbase          |
| Cassandra      |
| GoogleBigTable |
| Vertica        |
  
## Document Database
 JSON, BSON, XML 등 문서 지향 형식의 데이터를 저장하고 관리하는 Database 모델이다.

| 종류              |
| --------------- |
| MongoDB         |
| CouchDB         |
| Riak            |
| Azure Cosmos DB |
  
## Graph Database
 노드, 엣지, 속성으로 구성된 그래프 구조를 사용하여 데이터를 저장하고 관리하는 Database 모델이다.

| 종류           |
| ------------ |
| Sones        |
| AllegroGraph |
| neo4j        |
| BlazeGraph   |
| OrientDB     |

---
  
# 연결문서
