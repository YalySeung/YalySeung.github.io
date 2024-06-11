---
title : "WebStorm"
excerpt : "WebStorm"
toc : true
toc_sticky : true
toc_label : "WebStorm"
categories:
- IDE
tags:
- [환경, IDE]
last_modified_at: 2023-10-26T08:00:00-10:00:00
---
  
---
  
> **WebStorm 이란?**  
>
> javascript 개발 IDE로 React, Vue 등의 FrontEnd Framework를 사용하여 개발할때 사용한다. 
{: .notice--info}  
  
## 설치
  
```bash
npm i -g live-server
```
  
## 실행
  
```bash
live-server
```
  
## yarn 설치 및 환경 설정
  
![image](../../assets/images/yarn_version_error.png)

> **caution**
>
> yarn 설치 후 환경변수를 등록해주어야 하며, 환경변수는 셋팅 후 재기동 해주어야 적용된다. 
{: .notice--info}  
  
## 환경변수 등록 방법
설치된 Yarn 경로는 아래와 같다.
  
![image](../../assets/images/yarn_setup_output.png)

환경변수를 **Yarn의 bin** 경로로 잡아준다.
  
![image](../../assets/images/EnvironmentYarnModule.png)

> **memo**
>
> .yarn 에 cache 폴더가 생성되지 않을 경우 yarn 버전을 변경해준다. 
{: .notice--info}  

[Yarn](../../frontend/frontend-Yarn#yarn-버전-변경)
  
![image](../../assets/images/Pasted%20image%2020240503004421.png)
  
---
  
# 연결문서
- [npm](../../nodejs/nodejs-npm)
- [Vue-프로젝트-Init](../../vuestudy/vuestudy-Vue-프로젝트-Init)
- [React-Init](../../reactstudy/reactstudy-React-Init)
- [Yarn](../../frontend/frontend-Yarn)