---
title : "HTTP"
excerpt : "HTTP"
toc : true
toc_sticky : true
toc_label : "HTTP"
categories:
- ServerCommon
tags:
- [ServerCommon]
last_modified_at: 2023-11-26T08:00:00-10:00:00
---

# 날짜 : 2023-11-26 23:47

# 태그 : #ServerCommon
---

# 내용

## 정의
> HTTP란?
>Hyper Text Transfer Protocol
>브라우저와 서버가 통신할 수 있도록 만들어주는 여러 프로토콜 가운데 한 종류
>웹 브라우저와 웹 서버 사이에 HTML 문서를 주고받는데 쓰이는 통신 프로토콜
>최근에는 text, JSON, XML 등 다양한 데이터 송수신 가능

## 특징

### 클라이언트 서버 구조
- 클라이언트가 서버에 요청을 보내면 서버는 그에 대한 응답을 반환하는 클라이언트-서버 구조로 이루어짐

### 무상태 프로토콜(Stateless)
- 서버가 클라이언트의 상태를 보존하지 않는 무상태 프로토콜
- 클라이언트가 요청했던 history 보존 X

### 비 연결성(Connectionless)
- 연결을 유지하지 않음
- 일반적으로 초 단위 이하의 빠른 속도로 응답
- 트래픽이 많고 큰 규모의 서비스를 운영할 때는 비연결성은 한계가 드러남

### 단순함, 확장가능
- 구조가 단순하고 확장에 용이함.

---

# 연결문서
- [HTTP Request](../../ServerCommon/ServerCommon-HTTP-Request)