---
title : "React-vite-ProjectStruct"
excerpt : "React-vite-ProjectStruct"
toc : true
toc_sticky : true
toc_label : "React-vite-ProjectStruct"
categories:
- ReactStudy
tags:
- [React, FrontEnd, Study]
last_modified_at: 2023-10-22T08:00:00-10:00:00
---

# 날짜 : 2023-10-22 21:01

# 태그 : #React #FrontEnd #Study 
---

# 내용

## 프로젝트 구조

### 폴더 구조
  
![image](../../assets/images/ProjectStructure.png)

#### node_module
- 프로젝트에 필요한 패키지가 실제 설치된 디렉토리

#### public
- 서버 절대경로 기준으로 리소스 파일 가져올 때 사용하는 디렉토리

#### src
- 소스 디렉토리

##### assets
- 정적 이미지 파일 저장 디렉토리

### 파일 구조

#### .eslintrc.cjs
- eslint 설정파일

#### index.html
- React 프로젝트가 작동하는 기준 HTML

#### package-lock.json
- package.json의 상세 내역
- **build 할 때 필요**

#### package.json
- 프로젝트에 관한 각종 정보를 요약한 명세서
- **build 할 때 필요**

#### vite.config.js
- vite 설정파일

#### \*.css
- css 파일은 담당하는 jsx 파일과 파일명을 일치해서 사용
- App.css : App.jsx 파일의 지역 스타일
- index.css : index.html에 사용되는 전역 스타일

#### main.jsx
- 프로젝트의 시작점

#### App.jsx
- 애플리케이션의 최상위 컴포넌트

---

# 연결문서
