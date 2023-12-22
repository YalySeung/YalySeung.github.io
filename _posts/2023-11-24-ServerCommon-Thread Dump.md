---
title : "Thread Dump"
excerpt : "Thread Dump"
toc : true
toc_sticky : true
toc_label : "Thread Dump"
categories:
- ServerCommon
tags:
- [ServerCommon, java]
last_modified_at: 2023-11-24T08:00:00-10:00:00
---

# 날짜 : 2023-11-24 14:37

# 태그 : #ServerCommon #java
---

# 내용

## 정의
> Thread Dump란?
>프로세스에 속한 모든 쓰레드들의 상태를 기록한 것

## 특징
- 각 쓰레드들은 stack trace의 형태로 보여짐
- 발생된 문제들을 분석할 수 있는 데이터 제공
- 응용프로그램과 JVM 성능을 최적화 하는데 도움을 주는 정보 포함

## 쓰레드 종류와 상태
- [Thread 종류](../../servercommon/servercommon-Thread#종류)
- [Thread 상태](../../servercommon/servercommon-Thread#state)

## MAT

### 정의
> MAT란?
>Eclipse Memory Analizer
>dump 파일 분석 툴

### 사용방법

#### dump 파일 로드
  
![image](../../assets/images/MATOpenHeapDump.png)
- 팝업된 윈도우 탐색기에서 .hprof 파일을 선택한다.
- MAT가 해당 덤프파일을 분석하여 결과를 보여준다.

### 분석

#### dominator_tree
  
![image](../../assets/images/MATDominator_tree.png)

##### 각 항목 설명
* Retained Heap : 해당 오브젝트와 연결된 모든 객체를 포함한 메모리 점유량, GC에 의해 해제되지 않은 메모리 량
* Shallow Heap : 해당 오브젝트가 단독으로 차지하는 메모리, GC에 의해 해제되지 않은 메모리 량
* outgoing reference : 해당 객체가 참조하고 있는 객체
* incoming reference : 해당 객체를 참조하고 있는 객체

---

# 연결문서
- [Thread](../../servercommon/servercommon-Thread)