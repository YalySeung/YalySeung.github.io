---
title : "React Init"
excerpt : "React Init"
toc : true
toc_sticky : true
toc_label : "React Init"
categories:
- ReactStudy
tags:
- [React, 환경, FrontEnd, Study]
last_modified_at: 2023-10-19T08:00:00-10:00:00
---
  
---
  
 이 글에서는 WebStorm을 사용한 React Vite 프로젝트를 구성해볼 예정이다.

> **Vite 란?**  
>
> 네이티브 ESM(EcmaScript Modules)를 사용하여 빠른 개발 서버와 Module Hot Replacement를 제공하는 웹 개발 빌드 도구이다. 
{: .notice--info}  
  
## NodeJs 설치
 Vite는 NodeJs 환경에서 동작하니 먼저 nodejs를 설치하자. [Node 공식 홈페이지](https://nodejs.org/en/download/prebuilt-installer) 에서 Prebuild Installer를 다운로드 하여 설치한다. 

> **tip**
>
> Nodejs를 설치할 때, Tool for Native Modules의 자동 설치 옵션을 활성화 하면 애드온을 작성하거나 컴파일해야 할 때 필요한 도구 및 컴파일러 세트가 설치 된다. 
{: .notice--info}  
  
## vite 프로젝트 생성
 먼저 WebStorm을 실행하여 빈 프로젝트를 생성한다. Ctrl + \` 로 Terminal을 열어주고 NodeJs 가 잘 설치됐는지 확인한다.
  
```bash
node -v
```

 버전정보가 콘솔에 출력된다면 정상적으로 설치된 것이다. 이제 프로젝트를 생성한다. 
  
```bash
npm init vite@latest
```
  
![image](../../assets/images/NpmInitReact.png)
- **Framework** : React, Variant: Javascript + SWC[^1]
  
![image](../../assets/images/NpmInitJavaScript.png)
- **npm install** : dependency 다운로드
- **npm i** : dependency 다운로드
- **npm run dev** : 프로젝트 실행
  
## React 개발 환경 구성(npx)
  
### 환경셋팅
- node.js 설치
- 환경변수 등록
- npx create-react-app [프로젝트명]
  
#### React Developer Tool
- 크롬 확장 프로그램
- 시크릿모드에서 허용 및 파일 URL 엑세스 허용 체크
- 리액트 사용 페이지에 접속하면 파랗게 활성화됨
  
![image](../../assets/images/ReactDevelopToolActive.png)
- dev 모드로 진입하면 주황색으로 변경됨
  
![image](../../assets/images/ReactDevelopToolActiveDEV.png)
- Component 구조 확인
  
![image](../../assets/images/ExtensionComponentStruct.png)

---
  
# 연결문서
- [npm](../../nodejs/nodejs-npm)
- [vite](../../webcommon/webcommon-vite)