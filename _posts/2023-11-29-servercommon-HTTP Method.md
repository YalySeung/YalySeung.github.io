---
title : "HTTP Method"
excerpt : "HTTP Method"
toc : true
toc_sticky : true
toc_label : "HTTP Method"
categories:
- ServerCommon
tags:
- [ServerCommon]
last_modified_at: 2023-11-29T08:00:00-10:00:00
---
  
---
  
## GET
- 특정 리소스를 받기 위한 요청
- 리소스 생성, 수정, 삭제 등에 사용하면 안됨
  
## POST
- 리소스를 생성, 컨트롤러 실행을 위한 요청
  
## PUT
- 변경 가능한 리소스를 업데이트 하기 위한 요청
- 항상 리소스 식별 정보를 포함해야 함
  
## PATCH
- 변경 가능한 리소스의 부분 업데이트를 하기 위한 요청
- 항상 리소스 식별 정보를 포함해야 함
- PUT을 사용해 전체 객체를 업데이트하는 것이 관계여서 거의 사용되지 않음
  
## DELETE
- 특정 리소스를 제거하기 위한 요청
- 일반적으로 Request Body가 아닌 URI 경로에 제거하려는 리소스의 ID를 전달
  
## HEAD
- 클라이언트가 본분 없이 리소스에 대한 헤더만 검색 하는 요청
- 일반적으로 클라이언트가 서버에 리소스 유무 확인, 메타데이터 Read시 사용
  
## OPTIONS
- 클라이언트가 서버의 리소스에 대해 수행 가능한 동작을 알아보기 위한 요청
- 일반적으로 서버는 이 리소스에 대해 사용할 수 있는 HTTP 요청 메서드를 포함하는 Allow 헤더를 반환

---
  
# 연결문서
- [HTTP](../../servercommon/servercommon-HTTP)
- [Restful](../../servercommon/servercommon-Restful)