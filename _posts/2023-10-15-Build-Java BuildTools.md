---
title : "Java BuildTools"
excerpt : "Java BuildTools"
toc : true
toc_sticky : true
toc_label : "Java BuildTools"
categories:
- Build
tags:
- [Build]
last_modified_at: 2023-10-15T08:00:00-10:00:00
---

# 날짜 : 2023-10-15 10:01

# 태그 : #Build
---

# 내용

## 빌드 자동화 시스템

### Ant
- XML 기반
- 빌드 단위 지정 가능
- 간단하고 사용 편함
- 유연하지만 프로젝트 크기에 따라 빌드과정이 복잡해짐
- 생명주기가 없어 각각 결과물에 대한 의존관계 정의 필요

### Maven
- XML 기반
- 생명주기와 프로젝트 객체 모델이란 개념 도입
- Ant의 빌드 스크립트 개선
- pom.xml에 필요한 라이브러리 명시
- 학습필요
- 라이브러리가 상호 의존하는 경우 복잡도 증가

### Gradle
- Groovy 기반
- 변경된 부분만 빌드 가능
- 병렬처리로 빌드시간 단축
- 선언적 언어 사용으로 빌드 프로세스를 이해하고 관리하기 쉬움
- [Gradle](../../build/Build-Gradle)

## 역할
- 의존성 관리
- 동시에 여러 개발환경 지원
- 빌드 시간 단축
- 테스트 자동화 지원

---

# 연결문서
