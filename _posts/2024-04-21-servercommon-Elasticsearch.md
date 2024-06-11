---
title : "Elasticsearch"
excerpt : "Elasticsearch"
toc : true
toc_sticky : true
toc_label : "Elasticsearch"
categories:
- ServerCommon
tags:
- [ServerCommon]
last_modified_at: 2024-04-21T08:00:00-10:00:00
---
  
---
  
## 정의
> **Elasticsearch란**  
>
> Apache Lucene 기반의 java 오픈소스 분산 검색 엔진 
{: .notice--info}  

> **ELK 스택이란?**  
>
> Elasticsearch / Logstash / Kibana 를 사용하는 프로젝트 구조 
{: .notice--info}  

> **LogStash**  
>
> 다양한 소스(DB, csv파일)의 로그 또는 트랜잭션 데이터를 수집, 집계 파싱 
{: .notice--info}  

> **Kibana**  
>
> 데이터 시각화 및 모니터링 
{: .notice--info}  
  
## 특징
- **Scale Out** - shard를 통해 규모가 수평적으로 늘어날 수 있음
- **고가용성** - Replica를 통한 데이터 안정성 보장
- **Schema Free** - Json 문서를 기반으로 하여 스키마의 개념이 없음
- **Restful** - CRUD 작업은 HTTP Restful API를 통해 수행
  
## Concept
  
### Concept with RDBMS

| 개념     | RDBMS    | Elasticsearch |
| ------ | -------- | ------------- |
| 데이터베이스 | Database | Index         |
| 테이블    | Table    | Type          |
| 행      | Row      | Document      |
| 열      | Column   | Field         |
  
### Base Concept
  
#### Cluster
- Elasticsearch에서 가장 큰 시스템 단위
- 최소 하나 이상의 노드로 이루어진 노드들의 집합
- 클러스터 하나는 독립적인 시스템으로 유지됨
  
#### Node
- Elasticsearch를 구성하는 하나의 단위 프로세스
- 역할에 따라 Master-eligible, Data, Ingest, Tribe 노드로 구분됨

| Node Name         | 역할                                                   |
| ----------------- | ---------------------------------------------------- |
| Master-eligible   | 인덱스 생성 및 삭제, Cluster 노드들의 추적 및 관리, 데이터 입력시 할당할 샤드 배정 |
| Data              | CRUD와 관련된 Node, 자원소모가 많아 모니터링 필요                     |
| Ingest            | 데이터 변환, 사전처리 파이프라인 실행                                |
| Coordination only | 로드밸런서 역할 수행                                          |
  
#### Index
- RDBMS의 database와 대응
  
#### sharding
- 데이터를 분산해서 저장하는 방법
- index를 여러개의 shard로 분리
- 기본적으로 1개 존재
- 검색 성능 향상을 위해 개수 조정
  
#### replica
- shard의 복사본
- 노드 손실 시, 데이터 신뢰성 보장
  
---
  
# 연결문서
