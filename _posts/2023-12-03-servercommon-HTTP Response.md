---
title : "HTTP Response"
excerpt : "HTTP Response"
toc : true
toc_sticky : true
toc_label : "HTTP Response"
categories:
- ServerCommon
tags:
- [ServerCommon]
last_modified_at: 2023-12-03T08:00:00-10:00:00
---
  
---
  
![image](../../assets/images/HTTPResponse.png)
  
## 상태줄
- HTTP 응답의 시작 줄
- HTTP 버전 : 보통 HTTP/1.1
- 상태 코드 : 요청의 성공 또는 실패를 나타내는 숫자 코드
- 상태 텍스트 : 짧고 간결하게 상태 코드에 대한 설명을 나타낸 글
  
## Header
  
### Response Header Fields
- 서버 상태에 대한 추가정보를 제공

| Header 명                   | 설명                                                                       |
| --------------------------- | -------------------------------------------------------------------------- |
| Access-Control-Allow-Origin | 요청 Host와 응답 Host가 다를 경우 이 헤더에 프론트 주소를 적으면 에러 방지 |
| Set-Cookie                  | 서버에서 클라이언트에게 세션 쿠키 정보를 설정할때 사용                     |
  
### General Header Fields
- 메시지 전체에 적용되는 헤더

| Header 명 | 설명                                                                                                                                                         |
| --------- |:------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Server    | 웹 서버 정보                                                                                                                                                 |
| Via       | 요청헤더와 응답헤더에 포워드 프록시와 리버스 프록시에 의해서 추가. 포워드 메시지를 추적, 요청 루프 방지, 요청과 응답 체인에 따라 송신자의 프로토콜 정보 식별 |
  
### Entity Header Fields
- 요청 본문에 적용되는 헤더

| Header 명        | 설명                                     |
| ---------------- | ---------------------------------------- |
| Content-Encoding | 응답 콘텐츠를 압축하는 방식              |
| Content-Type     | 반환된 콘텐츠 타입을 클라이언트에게 전달 |
| Date             | 날짜                                     |
| Last-Modified    | 요청한 파일의 최종 수정일                |
  
## Body
- 응답의 실제 내용을 담고 있느 부분

---
  
# 연결문서
- [HTTP](../../servercommon/servercommon-HTTP)
- [HTTP Method](../../servercommon/servercommon-HTTP-Method)
- [HTTP Request](../../servercommon/servercommon-HTTP-Request)