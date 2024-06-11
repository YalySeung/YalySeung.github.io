---
title : "Files.walk()"
excerpt : "Files.walk()"
toc : true
toc_sticky : true
toc_label : "Files.walk()"
categories:
- java
tags:
- [프로그래밍언어, java, 미완료]
last_modified_at: 2024-06-07T08:00:00-10:00:00
---
  
---
  
 이 글에서는 디렉토리 검색에 필요한 **Files.walk API**에 대해서 알아보도록 하겠다.

 Web Application을 개발하다보면 **파일**이나 **디렉토리**에 대한 **검색**, **이동**, **삭제** 등의 처리를 해야 할 경우가 있다. 이 때, 유용하게 사용할 수 있는 API가 바로 Files.walk 이다. 이제부터 이 API의 사용법을 알아보도록 하겠다.
 
  **Files.walk(Path)**는 기본적으로 하위의 **모든 개체를 탐색**하며, **Files.work(Path, depth)**는 **depth 깊이만큼 만 탐색**한다. Files.walk는 Stream을 반환하기 때문에 filter, map 등을 사용하여 원하는 데이터를 추출하고, collect 하면 된다.

---
  
# 연결문서
