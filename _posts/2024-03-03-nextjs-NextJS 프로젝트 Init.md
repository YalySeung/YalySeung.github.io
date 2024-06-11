---
title : "NextJS 프로젝트 Init"
excerpt : "NextJS 프로젝트 Init"
toc : true
toc_sticky : true
toc_label : "NextJS 프로젝트 Init"
categories:
- NextJS
tags:
- [FrontEnd, NextJS]
last_modified_at: 2024-03-03T08:00:00-10:00:00
---
  
---
  
## Project Init
  
### 1. 빈 프로젝트 폴더 생성
  
### 2. terminal 에서 초기화 - package.js 파일 생성
  
```bash
npm init -y
```
  
### 3. 필요한 라이브러리 install
  
```bash
npm install react@latest next@latest react-dom@latest
```
  
### 4. package.json 수정
  
```json
{  
  "name": "nomadsample",  
  "version": "1.0.0",  
  "main": "index.js",  
  "scripts": {  
    "dev": "next dev"  
  },  
  "author": "",  
  "license": "ISC",  
  "keywords": [],  
  "description": "",  
  "dependencies": {  
    "next": "^14.1.1",  
    "react": "^18.2.0",  
    "react-dom": "^18.2.0"  
  }  
}
```  
- scripts는 프로젝트 실행시, 호출하는 script 이다.

> **tip**
>
> 이제 프로젝트를 npm run dev 로 실행할 수 있다! 
{: .notice--primary}  
  
### 5. 프로젝트 구조
  
![image](../../assets/images/NextJSProjectStructure.png)
- **app** : 페이지 관련 파일들이 있는 code region
- components : page에서 사용할 Component region
- package.json : package 정보 file
- package-lock.json :  package 버전 lock file

---
  
# 연결문서
- [npm](../../nodejs/nodejs-npm)