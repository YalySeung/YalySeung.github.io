---
title : "Servlet Container"
excerpt : "Servlet Container"
toc : true
toc_sticky : true
toc_label : "Servlet Container"
categories:
- Spring
tags:
- [Spring]
last_modified_at: 2023-10-25T08:00:00-10:00:00
---

# 날짜 : 2023-10-25 16:39

# 태그 : #Spring
---

# 내용

##  Servlet Container란
- 구현되어 있는 servlet 클래스의 규칙에 맞게 서블릿을 담고 관리해주는 컨테이너
- 사용자가 요청을 보내면 컨테이너는 HttpServletRequest, HttpServletResponse 두 객체를 생성하여 post, get 여부에 따라 동적 페이지를 생성하여 응답을 보낸다.

## 기능

### web server와 통신 지원
- 일반적으로 웹서버와 통신을 위해 listen, accept를 해야 하지만 이런 기능을 API로 제공

### Servlet lifecycle 관리
- Servlet 클래스를 인스턴스화, 초기화, 서블릿 메서드 호출, 해제 하는 일련의 과정을 관리해준다.

### multi thread 지원 및 관리
- request 마다 새로운 thread 를 생성
- 서비스 메소드를 실행하고 나면 thread가 종료됨

---

# 연결문서
- [Servlet](../../Spring/Spring-Servlet)