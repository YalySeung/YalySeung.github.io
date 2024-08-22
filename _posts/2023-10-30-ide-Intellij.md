---
title : "Intellij"
excerpt : "Intellij"
toc : true
toc_sticky : true
toc_label : "Intellij"
categories:
- IDE
tags:
- [환경, IDE]
last_modified_at: 2023-10-30T08:00:00-10:00:00
---
  
---
  
### 인코딩 설정
  
#### vmoption 변경
- 경로 : C:\Program Files\JetBrains\IntelliJ IDEA 2022.2.3\bin\idea64.exe.vmoptions
```  
-Dfile.encoding=UTF-8
```
  
#### 파일 인코딩 변경
  
![image](../../assets/images/IntelliJSetFileEncoding.png)
  
#### WAS 인코딩 변경
  
![image](../../assets/images/IntellijSetWASEncoding.png)
  
### Git 파일 변경 사항 보기
  
![image](../../assets/images/IntelliJGitSetting.png)
Use non-modal commit interface 항목을 체크 해제하면 **LocalChanges** 항목을 확인 할 수 있다.
  
### Live Template
사용자 템플릿을 정의하여 자동완성하는 기능을 사용할 수 있다. 예를 들면 psvm를 입력 할 경우 public static void Main 이 자동완성 되는 기능이다.
  
![image](../../assets/images/liveTemplate.png)
Live Template 기능을 사용하는 방법은 아래와 같다.
1. IntelliJ Setting - Live Template로 이동한다.
2. '+' 버튼으로 새 Live Tempate 항목을 추가한다.
3. Template Name, Description, Content, Scope를 설정한다.
4. 필요에 따라 변수도 추가 가능하다.
5. 에디터에서 Template Name을 입력하면 Content가 자동완성 되어 입력된다.
  
### AnnotationProcessor
AnnotationProcessor는 [Compile](../../developcommon/developcommon-Compile) 타임에 특정 라이브러리에서 사용하는 Annotation을 스캔하여 [Boiler Plate](../../cleancode/cleancode-Boiler-Plate)를 생성한다. AnnotationProcessor를 사용하는 라이브러리는 대표적으로 [Lombok](../../spring/spring-Lombok), [Querydsl](../../jpa/jpa-Querydsl) 이 있다. Intellij에서 AnnotationProcessor를 활성화 하는 방법은 아래와 같다.
1. Settings > AnnotationProcessor 메뉴 선택
2. [AnnotationProcessor](../../spring/spring-AnnotationProcessor) 활성화
  
![image](../../assets/images/AnnotationProcessor.png)
  
### 파일 복구
Git Commit 전에 Remote fetch를 해서 Commit 안한 로컬 변경 파일들이 모두 날아갔다.. 우리 IntetlliJ에게는 히스토리 관리하는 기능이 분명이 있을것이라고 확신하고 구글링하여 모두 복구 완료했다. 지워진 파일 복구 방법은 아래와 같다.
  
![image](../../assets/images/LocalHistoryRevert.png)
1. 프로젝트 **탐색기에서 되돌리고 싶은 폴더를 찾아 우클릭** > LocalHistory > Show History 항목으로 이동한다.
2. 윈도우가 팝업되고, 좌측 리스트에 시간대별 파일 스냅샷이 저장되어있다. 되돌리고싶은 시점의 항목에서 우클릭 > Revert 를 선택한다.

복구완료!

---
  
# 연결문서
- [Git-SSH Config](../../git/git-Git-SSH-Config)- [Git-SSH Config](../../git/git-Git-SSH-Config)
- [AnnotationProcessor](../../spring/spring-AnnotationProcessor)