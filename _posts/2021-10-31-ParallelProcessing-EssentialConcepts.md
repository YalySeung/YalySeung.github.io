---
title: "Essential Concepts"
excerpt: "병렬처리 관련된 용어들"

categories:
  - Parallel Processing

tags:
  - [Parallel Processing]

toc: true
toc_sticky: true
toc_label: "Essential Concepts"

last_modified_at: 2021-10-07T08:00:00-10:00:00
---

# 동시성(Concurrency)과 병렬성(Parallelism)
  - 동시성(Concurrency) : 여러 일을 한꺼번에 다루는데 관련된 것
  - 병렬성(Parallelism) : 여러 일을 한꺼번에 "실행" 하는데 관련된 것

# 공유메모리와 분산메모리
  - 공유메모리 : 프로세서 사이의 커뮤니케이션이 메모리 자체를 통해 이루어짐
  - 분산메모리 : 프로세서 사이의 커뮤니케이션이 네트워크를 통해 이루어짐(프로세서가 많을수록 효과적)

# 멀티쓰레드 프로그래밍 모델
  - Thread 와 Lock
  - 함수형 프로그래밍
  - 클로저
  - 액터
  - 순차 프로세스 통신(CSP)
  - 데이터 병렬성
  - 람다 아키텍처


이후로 위의 모델들에 관련된 내용을 포스팅 할 예정이다.

# 참고문헌
「<cite>폴 부처</cite> --- 7가지 동시성 모델. 임백준. 한빛미디어, 2016」
