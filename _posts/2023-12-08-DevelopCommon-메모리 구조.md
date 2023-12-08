---
title : "메모리 구조"
excerpt : "메모리 구조"
toc : true
toc_sticky : true
toc_label : "메모리 구조"
categories:
- DevelopCommon
tags:
- [DevelopCommon]
last_modified_at: 2023-12-08T08:00:00-10:00:00
---

# 날짜 : 2023-12-08 11:16

# 태그 : #DevelopCommon
---

# 내용

## 메모리 구조
![image](./../../assets/images/MemoryStructure.png){: width="60%" height="60%"} 

### Code영역
- 프로그램의 소스코드가 저장되는 영역
- 함수, 제어문, 상수등의 영역

### Data 영역
- 전역변수, Static 변수가 저장되는 영역
- 프로그램 시작과 동시에 할당, 종료 후 소멸

### Heap 영역
- 프로그래머가 할당, 해제하는 메모리 공간
- 동적 할당시, 사용하는 영역
- 클래스, 클로저 등..
- 런타임에 크기 결정

### Stack 영역
- 프로그램의 임시 메모리 영역
- 함수 호출 시 생성되는 지역변수, 배개변수 저장
- 함수 종료 후 소멸

---

# 연결문서
- [heap](../../자료구조/자료구조-heap)