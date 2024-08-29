---
title : "SourceTree Error"
excerpt : "SourceTree Error"
toc : true
toc_sticky : true
toc_label : "SourceTree Error"
categories:
- SourceTree
tags:
- [SourceTree]
last_modified_at: 2023-12-30T08:00:00-10:00:00
---
  
---
  
## 로그확인 방법
- 로그파일 경로 : C:\\Users\\<사용자명>\\AppData\\Local\\Atlassian\\SourceTree
  
![image](../../assets/images/SourceTreeLogPath.png)
  
## 에러 별 조치
  
### 로고 팝업창 이후 아무런 동작 없음
- 소스트리를 한동안 사용하지 않다가 사용할 경우 종종 발생하는 현상
  
#### 캐시 삭제
- 소스트리 구성에 필요한 cache 파일이 원인인 경우가 대부분이다.
- C:\\Users\<사용자명>\AppData\\Local\\Atlassian\SourceTree.exe_Url_<식별자>\\3.3.8.3848\\Composition.cache **파일 삭제**
  
![image](../../assets/images/SourceTreeCache.png)
  
---
  
# 연결문서
