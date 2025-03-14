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
  
 이 글에서는 HTTP 요청에 사용되는 Method들에 대해 알아보겠다.
  
## GET
 특정 **리소스를 받고 싶을 때 사용**하는 메서드로 요청시 필요한 정보는 query parameter로 전달한다. 관례적으로 리소스 생성, 수정, 삭제에는 사용하지 않는다.
  
## POST
 **리소스 생성, 컨트롤러 실행을 위한 요청시 사용**하는 메서드로, 요청시 필요한 정보는 request body에 전달한다.
  
## PUT
 변경 가능한 **리소스 전체를 업데이트** 하기 위한 메서드로 요청시 필요한 정보는 request body에 전달한다. PUT 메서드는 업데이트 할 리소스 식별 정보를 포함해야 한다.
  
## PATCH
 변경 가능한 **리소스의 부분 업데이트**를 하기 위한 메서드로 PUT메서드와 마찬가지로 항상 리소스 식별 정보를 포함해야 한다. PUT을 사용해 전체 객체를 업데이트하는 것이 관례여엿 거의 사용되지 않는다.
  
## DELETE
 특정 **리소스를 제거**하기 위한 메서드로 일반적으로는 Request Body가 아닌 URI 경로에 제거하려는 리소스의 ID를 전달한다.
  
## HEAD
 클라이언트가 **본분 없이 리소스에 대한 헤더를 검색** 하는 메서드로 일반적으로 클라이언트가 서버에 리소스 유무 확인하고 메타데이터를 Read할때 사용한다.
  
## OPTIONS
 클라이언트가 **서버의 리소스에 대해 수행 가능한 동작을 알아보기 위한 메서드**이다. 일반적으로 서버는 이 리소스에 대해 사용할 수 있는 HTTP 요청 메서드를 포함하는 Allow 헤더를 반환한다.

---
  
# 연결문서
- [HTTP](../../servercommon/servercommon-HTTP)
- [Restful](../../servercommon/servercommon-Restful)