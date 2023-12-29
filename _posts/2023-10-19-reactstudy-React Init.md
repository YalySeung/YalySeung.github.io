---
title : "React Init"
excerpt : "React Init"
toc : true
toc_sticky : true
toc_label : "React Init"
categories:
- ReactStudy
tags:
- [React, Lecture, 환경구성, FrontEnd, Study]
last_modified_at: 2023-10-19T08:00:00-10:00:00
---

# 날짜 : 2023-10-19 15:46

# 태그 : #React #Lecture #환경구성 #FrontEnd #Study 
---

# 내용

## React 개발 환경 구성(vite)

### Tool 설치
- nodejs 설치

#### React Developer Tool
- 크롬 확장 프로그램
- 시크릿모드에서 허용 및 파일 URL 엑세스 허용 체크
- 리액트 사용 페이지에 접속하면 파랗게 활성화됨
  
![image](../../assets/images/ReactDevelopToolActive.png)
- dev 모드로 진입하면 주황색으로 변경됨
  
![image](../../assets/images/ReactDevelopToolActiveDEV.png)
- Component 구조 확인
  
![image](../../assets/images/ExtensionComponentStruct.png)

### 프로젝트 초기화
- **npm init vite@latest** : 프로젝트 생성
  
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

---

# 연결문서
- [npm](../../nodejs/nodejs-npm)
- [vite](../../webcommon/webcommon-vite)