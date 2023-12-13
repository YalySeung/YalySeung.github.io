---
title : "HTTP Request"
excerpt : "HTTP Request"
toc : true
toc_sticky : true
toc_label : "HTTP Request"
categories:
- ServerCommon
tags:
- [ServerCommon]
last_modified_at: 2023-11-29T08:00:00-10:00:00
---

# 날짜 : 2023-11-29 18:13

# 태그 : #ServerCommon
---

# 내용
  
![image](../../assets/Images/HTTPRequest.png)

## 첫째줄 
- [HTTP Method](../../ServerCommon/ServerCommon-HTTP-Method) : 서버가 수행해야 할 동작을 나타냄
- URI : URL, 프로토콜, 포트, 도메인등의 절대경로
- HTTP 버전 : 메시지의 남은 구조 결정, 응답 메시지에 사용할 HTTP 버전

## Header
- 대소문자를 구분하지 않는 이름, 콜론, 값으로 구성
- 값 앞의 공백은 무시됨
- 값까지 포함한 한줄로 구성되지만 꽤 길어질 수 있음
- 헤더는 Request, General, Entity 헤더로 부분으로 나뉨

### Request Header Fields
- 요청의 내용을 좀 더 구체화하고, 컨텍스트를 제공
- 조건부로 제한하여 요청의 내용을 수정

| Header 명         | 설명                                                                          |
| ----------------- |:----------------------------------------------------------------------------- |
| Host              | 서버의 도메인 이름(포트는 optional)                                           |
| User-Agent        | 사용자 에어전트의 브라우저, 운영체제, 플랫폼 및 버전                          |
| Accept            | 클라리언트가 허용하는 파일 형식 (MIME TYPE)                                   |
| Accept-Encoding   | 클라이언트가 허용하는 인코딩, 콘텐츠 압축방식                                 |
| Authorization     | 인증 토큰을 서버로 보낼때 사용하는 헤더, API 요청을 할 때, 토큰이 없으면 거절 |
| Origin            | POST와 같은 요청을 보낼 때, 요청이 어느 주소에서 시작되었는지 나타냄          |
| Referer           | 이전의 페이지 주소가 담겨있음                                                 |
| IF-Modified-Since | 최신 버전 페이지 요청을 위한 필드                                             |

### General Header Fields
- 메시지 전체에 적용되는 헤더

| Header 명  | 설명                                                                                                                                                         |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Connection | 현재 전송이 완료된 후 네트워크 접속을 유지할지 여부를 제어(keep-alive : 연결 지속)                                                                           |
| Via        | 요청헤더와 응답헤더에 포워드 프록시와 리버스 프록시에 의해서 추가. 포워드 메시지를 추적, 요청 루프 방지, 요청과 응답 체인에 따라 송신자의 프로토콜 정보 식별 |

### Entity 헤더
- 요청 분몬에 적용되는 헤더

| Header 명      | 설명                                                                              |
| -------------- | --------------------------------------------------------------------------------- |
| Content-Length | 요청과 응답 메시지의 본문 크기를 바이트 단위로 표시. 메시지 크기에 따라 자동 생성 |

---

# 연결문서
- [HTTP](../../ServerCommon/ServerCommon-HTTP)
- [HTTP Method](../../ServerCommon/ServerCommon-HTTP-Method)
- [HTTP Response](../../ServerCommon/ServerCommon-HTTP-Response)