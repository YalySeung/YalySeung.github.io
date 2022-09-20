---
title: "Thread In WPF"
excerpt: "WPF 에서 Thread" 

categories:
- C#

tags:
- [C#, WPF]

toc: true
toc_sticky: true
toc_label: "Thread In WPF"

last_modified_at: 2022-09-20T08:00:00-10:00:00
---
# STA
  - Single-Thread Apartment
  - STA 객체는 하나의 Thread(생성한)에서만 Access 가능

---
# WPF UI Thread의 특징
  - Main Thread가 모든 UI 작업 수행, 다른 Thread에서 Access 시, ThreadAbortException 발생
  - Main Thread는 WPF 객체들을 Dispatcher 큐 관리자의 작업을 처리, Frame 종료 전까지 UI를 그리지 않음

---

# Dispatcher
  - WPF 객체들을 독립적으로 관리하는 큐 관리자
  - FIFO 방식으로 UI 작업 실행
  - Queue 작업이 끝나기 전까지 UI 갱신 X

---

# DispatcherObject
  - STA 실행 Template Class
  - WPF의 UI 관련 요소들은 대부분 이 클래스를 상속
  - CheckAccess : 코드 객체를 사용할 수 있는 Thread인지 여부 반환
  - VerifyAccess : 코드가 객체를 사용하기 위한 올바른 Thread인지 판단

---

# Invoke & BeginInvoke
  - Dispatcher에 있는 메서드
  - Dispatcher가 속해있는 Thread에서 Main Thread로 작업 요청
  - Invoke : 동기
  - BeginInvoke : 비동기