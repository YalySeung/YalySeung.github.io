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

# 날짜 : 2023-10-30 23:43

# 태그 : #환경 #IDE
---

# 내용

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
- Use non-modal commit interface 항목을 체크 해제하면 LocalChanges 항목을 확인 할 수 있다.

### Live Template
- 사용자 템플릿을 정의하여 자동완성할 수 있는 기능
  
![image](../../assets/images/liveTemplate.png)
1. IntelliJ Setting - Live Template로 이동
2. '+' 버튼으로 새 Live Tempate 항목 추가
3. Template Name, Description, Content, Scope를 설정
4. 필요에 따라 변수도 추가 가능
5. 에디터에서 Template Name을 입력하면 Content가 자동완성 되어 입력됨

---

# 연결문서
