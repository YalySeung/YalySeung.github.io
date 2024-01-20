---
title : "Restful"
excerpt : "Restful"
toc : true
toc_sticky : true
toc_label : "Restful"
categories:
- ServerCommon
tags:
- [ServerCommon]
last_modified_at: 2023-12-08T08:00:00-10:00:00
---

# 날짜 : 2023-12-08 15:29

# 태그 : #ServerCommon 
---

# 내용

## 정의
> **Restful 이란?**
>
> Respresentational State Transfer
> 분산 하이퍼미디어 시스템을 위한 소프트웨어 아키텍처의 한 형식
{: .notice--info}

## 특징

### Uniform Interface
- URI로 지정한 리소스에 대한 조작을 통일성 있고 한정적인 인터페이스로 수행

### Stateless
- 사용자나 클라이언트의 컨텍스트를 서버쪽으로 유지하지 않는다.
- 세션이나 쿠키를 별도로 관리하지 않아, 구현이 단순하다.

### Cacheable
- HTTP 웹 표준을 그대로 사용하기때문에 HTTP가 가진 캐싱 기능을 사용 가능

### Self-descriptiveness
- REST API 메시지만으로 기능을 이해할 수 있다.

### Client-Server Architecture
- REST 서버는 API를 제공하고, 비즈니스 로직 처리 및 저장을 책임진다.
- 클라이언트는 사용자인증, 컨텍스트(세션, 로그인 정보)등을 직접 관리
- 서로간의 의존성 감소

### 계층구조
- 로드밸런싱, 암호화, 사용자 인증등을 추가하여 구조상의 유연성 제공

## RESTful 아키텍처
- URI가 정보의 <span style="color:red">자원</span>을 표현
- 자원에 대한 <span style="color:red">행위</span>는 [HTTP Method](../../servercommon/servercommon-HTTP-Method) (GET, POST, PUT, DELETE)로 표현
- 특정 행위의 <span style="color:red">표현</span>은 body를 이용(XML, JSON)
- 리소스 명은 명사를 사용
> **format**
>
> POST http://localhost/{Collection}/{Document}
{: .notice--info}

```

//직원정보 요청
GET http://localhost/worker/얄리

//직원정보 등록
POST http://localhost/worker
{
"name":"얄리",
"team":"연구1팀"
}

//직원정보 변경
PUT http://localhost/worker/얄리{
"team":"Q서비스팀"
}

//직원정보 제거
DELETE http://localhost/worker/얄리

## REST Resource(자원)
```

### Collection
- Document의 묶음

### Document
- 1개의 객체
- 일반적으로 리소스의 집합중 하나
- Collection 뒤에 위치

### Method(행위)
- [HTTP Method](../../servercommon/servercommon-HTTP-Method)
- POST : 리소스 생성
- GET : 리소스 조회
- PUT : 리소스 수정
- DELETE : 리소스 삭제

### Representation(표현)

```json
PUT http://localhost/worker/얄리{
//표현
"team":"Q서비스팀"
}
```

- body 부분이 표현에 해당한다.

## RESTful URI 규칙
- URI 마지막에 '/' 포함하지 않는다, 계층관계를 나타낼때만 사용
- '_' 언더바 대신 '-' 하이픈 사용
- 소문자 사용
- Method는 URI에 포함하지 않는다.
- 컨트롤 자원을 의미하는 URI에서는 동사 사용을 허용
- URI에 자원의 행위를 표시하지 않는다.
- 확장자 대신 Accept Header를 사용한다.

---

# 연결문서
- [HTTP Method](../../servercommon/servercommon-HTTP-Method)