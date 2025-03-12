---
title : "Swagger codeGen"
excerpt : "Swagger codeGen"
toc : true
toc_sticky : true
toc_label : "Swagger codeGen"
categories:
- DevelopCommon
tags:
- [DevelopCommon]
last_modified_at: 2024-11-01T08:00:00-10:00:00
---
  
---
  
 이 글에서는 Swagger-codegen-cli 라이브러리에 대해서 알아보겠다

 필자는 오늘도 금융권 SI 프로젝트를 수행하고 있다. 기존에 한땀한땀 엑셀에 작성했던 API 설계서를 좀 더 편리하게 작성하기 위해 프로젝트를 만들고 Swagger를 적용했다. 
 
 Local 서버를 기동하면 Swagger css 가 적용된 아름다운 API 문서를 접할 수 있지만, 산출물로 사용하려면 서버 프로세스를 기동하지 않고 문서를 확인할 수 있도록 standalone html 문서를 만들어야 했다. 
 
외부망을 자유롭게 사용할 수 있다면, 웹사이트에서 api-docs.json  파일을 손쉽게 변환 할 수 있겠지만 오늘도 폐쇄망에서 고통받는 필자는 Swagger-codegen-cli 라는 유틸리티 jar를 사용하기로 했다.

> **Swagger-codegen-cli란?**  
>
>Swagger/OpenAPI 명세를 기반으로 클라이언트 SDK, 서버 스텁 코드, 문서, 그리고 다양한 프로그래밍 언어와 프레임워크에 대한 코드 생성을 자동화하는 명령줄 도구이다 
{: .notice--info}  
  
## 사용법
 먼저 라이브러리 사용을 위해서 swagger-codegen-cli.jar 파일을 다운로드 받는다. 이 라이브러리는 오픈소스이므로 github 페이지에서 stable release 버전을 받으면 되겠다. 필자는 3.0.9 버전을 다운로드 받았다.

 그 다음은 api-docs.json 파을을 준비한다. 그리고 아래 명령어를 통해 결과물을 생성한다.
  
```bash
java -jar <codegen-cli 라이브러리 경로> generate -i <api-docs.json 경로> -l <생성 문서의 포멧> -o <output 폴더 경로>
```
  
## 지원 문서 타입
 swagger-codegen-cli.jar 에서는 아래와 같은 문서 타입을 지원한다.

| 타입              | cli            |
| --------------- | -------------- |
| .html           | html           |
| .html2          | html2          |
| MarkDown        | markdown       |
| Confluence Wiki | confluenceWiki |
| AsciiDoc        | asciidoc       |
| PlantUML        | plantuml       |
| Static Docs     | dynamic-html   |
  
---
  
# 연결문서
- [Swagger](../../servercommon/servercommon-Swagger)
- [CLI](../../cli/cli-CLI)