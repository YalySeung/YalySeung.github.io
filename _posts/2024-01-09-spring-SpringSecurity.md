---
title : "SpringSecurity"
excerpt : "SpringSecurity"
toc : true
toc_sticky : true
toc_label : "SpringSecurity"
categories:
- Spring
tags:
- [Spring]
last_modified_at: 2024-01-09T08:00:00-10:00:00
---

# 날짜 : 2024-01-09 15:16

# 태그 : #Spring
---

# 내용

##  정의
> **Spring Security란?**
>
> Spring 기반의 애플리케이션 보안을 담당하는 스프링 하위 프레임워크
{: .notice--info}

## 특징
- Spring Security는 기본적으로 인증 절차 후 인가 절차를 진행
- 인가 과정에서 해당 리소스에 대한 접근 권한이 있는지 확인
- Principal(접근 주체) 을 아이디로 Credential(비밀번호)을 비밀번호로 사용하는 Credential 기반의 인증방식 사용

## 주요 모듈

### SecurityContextHolder
- 보안 주체의 세부 정보를 포함하여 응용프로그램의 현재 보안 컨텍스트에 대한 세부 정보 저장

### SecurityContext
- Authentication을 보관하는 역할
- Authentication에 접근 가능

### Authentication
- 현재 접근하는 주체의 정보와 권한을 담는 Interface
- 이 객체를 SecurityContext에 저장됨

### AuthenticationProvider
- 실제 인증에 대한 부분을 처리
- 인증 전의 Authentication 객체를 받아 인증이 완료된 객체를 반환

### Authentication Manager
- 인증 프로세스를 관리
- AuthenticationProvider에게 인증을 위임하고, 인증이 성공하면 정보를 SecurityContext에 저장
- 인증상태를 보관하기 위해 세션에 인증정보 저장

### UserDetail
- 인증이 성공하여 생성된 사용자 정보 객체

---

# 연결문서
- [인증과 인가](../../servercommon/servercommon-인증과-인가)