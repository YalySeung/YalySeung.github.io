---
title : "Garbage Collection"
excerpt : "Garbage Collection"
toc : true
toc_sticky : true
toc_label : "Garbage Collection"
categories:
- DevelopCommon
tags:
- [DevelopCommon]
last_modified_at: 2023-12-08T08:00:00-10:00:00
---

# 날짜 : 2023-12-08 11:26

# 태그 : #DevelopCommon
---

# 내용

## 정의

> **Garbage Collection이란?**
>
> 자바의 메모리 관리 방법 중 하나로 JVM의 heap 영역에 동적으로 할당했던 메모리 중 필요없게 된 메모리 객체를 모아 주기적으로 제거하는 프로세스 
{: .notice--info}

## 장점
- 이미 해제 된 메모리에 접근 방지
- 이미 해제 된 메모리를 다시 해제 하는 버그 방지
- 메모리 누수 방지

## 단점
- 메모리 해제 타이밍 예측이 어려움
- Garbage Collection 이 일어나는 타이밍과 점유 시간 예측 어려움
- 객체가 필요 없어지는 시점을 프로그래머가 알고 있는 경우에도, 메모리 해제 시점을 추적해야 함

## Garbage 탐지
- Heap Memory 객체를 참조하는 Root 목록을 순회하며 참조 여부 확인
- Heap Memory 를 순회하며 Root 와 관계없는 객체 해제(Sweap)
- 인접한 객체들을 이동시켜 빈 공간을 채움(Compaction)
- 객체 이동이 끝나면 깨끗한 상태의 메모리를 얻음

## 세대별 Garbage Collection
- "생성된지 얼마 안된 객체들은 빨리 해제될 가능성이 높다" 라는 가정
- CLR은 메모리를 구역별로 나누어 메모리에서 빨리 해제될 객체와 오래 남아있을 객체를 따로 관리
- 0, 1, 2 세가지의 세대 존재, 숫자가 낮을 수 록 빨리 해제될 가능성이 높은 객체들을 관리
- 객체는 Garbage Collection을 겪은 횟수가 많을 수록, 높은 세대로 이동
- 각 세대의 임계치에 따라 Garbage Collection 수행
- 2세대 Heap Memory 가 가득차면, 어플리케이션을 일시중단, 모든 세대에 대해서 다시 GC 실행

---

# 연결문서
- [heap](../../자료구조/자료구조-heap)