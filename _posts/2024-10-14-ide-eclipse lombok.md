---
title : "eclipse lombok"
excerpt : "eclipse lombok"
toc : true
toc_sticky : true
toc_label : "eclipse lombok"
categories:
- IDE
tags:
- [IDE, eclipse]
last_modified_at: 2024-10-14T08:00:00-10:00:00
---
  
---
  
 이 글에서는 eclipse 에서 [Lombok](../../spring/spring-Lombok) 라이브러리를 사용하는 방법에 대해 알아보겠다.

 eclipse에서는 [Intellij](../../ide/ide-Intellij)와 같이 [Intellij](../../ide/ide-Intellij#annotationprocessor) 를 설정하여여 lombok을 사용하는 것이 아니라 **직접 lombok 라이브러리를 설치하고, IDE를 지정**해주어야 한다.

 먼저 설치를 위해 lombok 라이브리러리를 다운로드 받는다.

 Window Command 창에서 다운로드 받은 lombok jar 경로로 이동하여 아래 명령줄을 입력한다.
  
```bash
java -jar lombok.jar
```
  
![image](../../assets/images/lombokInstall.png)

 설치 팝업창이 뜨면, Specify location > eclipse exe 파일의 경로를 지정해준다.

 아래와 같이 eclipse 경로에 lombok jar 파일이 생성된다.
  
![image](../../assets/images/lombokIntallResult.png)

 이제 gradle에서 lombok 을 import 한 후 사용하면 된다.
 
---
  
# 연결문서
- [Intellij](../../ide/ide-Intellij#annotationprocessor)
- [Lombok](../../spring/spring-Lombok)