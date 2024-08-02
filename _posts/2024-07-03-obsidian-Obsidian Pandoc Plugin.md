---
title : "Obsidian Pandoc Plugin"
excerpt : "Obsidian Pandoc Plugin"
toc : true
toc_sticky : true
toc_label : "Obsidian Pandoc Plugin"
categories:
- Obsidian
tags:
- [Obsidian]
last_modified_at: 2024-07-03T08:00:00-10:00:00
---
  
---
  
> **Pandoc 이란?**  
>
> 마크다운, HTML, LaTeX 등 다양한 문서 형식을 상호 변환하는 도구로, 플러그인을 통해 추가 기능을 제공하고나 변환 과정을 커스터마이징 할 수 있다.
>  
{: .notice--info}  
  
## Pandoc 플러그인 둘러보기
 Obsidian에서 Pandoc 기능을 사용하기 위해서는 먼저 **Pandoc 커뮤니티 플러그인을 설치**해야한다. 
  
![image](../../assets/images/Pasted%20image%2020240703134510.png)
 설치를 완료했다면 플러그인을 활성화 하고, 옵션을 살펴보자.
  
![image](../../assets/images/PandocPluginOption.png)

 여기서 가장 중요한 부분은 **Pandoc exe 경로**와 **Extra Pandoc Argument**이다. Obsidian Pandoc 플러그인은 플러그인만 설치해서는 사용할 수 없다. 플러그인 사용을 위해 꼭 필요한 [Pandoc](https://pandoc.org/installing.html)을 **다운로드 받자**.
  
## Pandoc 사용 환경 설정하기
 다운로드 후 설치가 완료되면, **플러그인 옵션 중 Pandoc path**에 **Pandoc exe경로를 입력**해준다. 여기까지만 진행해도 Obsidian 메모를 다른 포맷으로 변환할 수 있다. 단지 결과물 디자인이 마음에 안 들 뿐이다. 

 필자는 Obsidian 메모형태로 메뉴얼을 작성하여 배포 할 예정이다. 메뉴얼은 역시 ms-word 이므로 **ms-word 템플릿을 사용한 스타일 적용 방법**을 알아보자.

 먼저 마음에 드는 템플릿을 공수하기 위해 [ms-word 템플릿 홈페이지](https://create.microsoft.com/ko-kr/word-%ED%85%9C%ED%94%8C%EB%A6%BF)에 접속한다. 이곳에서 마음에 드는 템플릿을 하나 다운로드 받아 옵시디언 vault 내의 마음에 드는 경로로 이동 시킨다. 파일명도 내가 식별하기 쉬운 것으로 변경한다. 필자 같은 경우 ToDo 라는 vault 경로의 Resources 폴더 아래 위치시켰다.
  
![image](../../assets/images/PandocResource.png)

 위 사진을 보면 템플릿 파일 이외에 **pandoc.yaml** 파일이 보일 것이다. 이 파일은 pandoc 실행 시 몇 가지 설정을 도와준다. 필자는 미리 파일을 생성해 놓았다. 여러분도 **새 파일을 생성하여 내용을 입력**하자.
  
```yaml
  
# pandoc.yaml
  
# 출력 형식과 파일
standalone: true
toc: true
  
# CSS 파일
css: "C:/WorkSpace/ToDo/98.Resources/pandoc/pandoc.css"
  
# Word Template
reference-doc: "C:/WorkSpace/ToDo/98.Resources/pandoc/wordtemplate.docx"
  
# 리소스 경로
resource-path: "C:/WorkSpace/ToDo"
```

| 설정 항목         | 기능                            |
| ------------- | ----------------------------- |
| standalone    | 출력 문서가 자체적으로 완전한 문서가 되도록 한다.  |
| toc           | 목차를 추가한다.                     |
| css           | html 로 export 할 경우 css를 적용한다. |
| reference-doc | 참조할 파일을 추가한다.                 |
| resource-path | 이미지 파일 경로를 추가한다.              |  

 이곳의 **reference-doc 항목에 위에서 다운 받아 놓은 템플릿 파일 경로를 지정**한다.
 이 이외에도 다른 옵션이 많이 있으므로 참고하길 바란다. ([공식문서](https://pandoc.org/MANUAL.html))

 설정 파일을 생성했다면 **Obsidian Pandoc 플러그인 옵션의 arguments 항목을 작성**한다.
  
![image](../../assets/images/PandocArgument.png)

이제 환경 설정이 모두 완료되었다.
  
## Pandoc Plugin 사용
 설정을 완료했으니 사용해보자.
 내가 변환하고 싶은 메모로 이동하여 **명령어 창**을 실행한다. 그리고 **export를 검색**하면 내가 변환할 수 있는 파일 포맷이 모두 보인다.
  
![image](../../assets/images/ObsidianPandocCommand.png)

 필자는 word로 변환할 것이므로 **Export as Word Document** 를 선택한다. 
  
![image](../../assets/images/PandocExportWord.png)

 필자가 설정했던 output 경로에 word 파일이 생성된 것으로 확인 할 수 있다.

---
  
# 연결문서
