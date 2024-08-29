---
title : "Yarn"
excerpt : "Yarn"
toc : true
toc_sticky : true
toc_label : "Yarn"
categories:
- FrontEnd
tags:
- [Yarn, BuildManager]
last_modified_at: 2024-05-02T08:00:00-10:00:00
---
  
---
  
## 정의
> **Yarn이란?**  
>
> Meta에서 만든 자바스크립트 패키지 매니저 
{: .notice--info}  
  
## 환경 설정
  
### 설치
  
```bash
npm install -g yarn
```
  
### 설치 확인
  
```bash
yarn --version
```
  
### yarn 버전 변경
  
```bash
yarn set version <버전정보>
yarn set version latest
yarn set version 3.x.x
```
  
## 사용법
  
### package.json 생성
  
```bash
yarn init
```
  
### package.json으로부터 의존성 모듈 설치
  
```bash
yarn install
```
  
### 패키지 명을 사용한 의존성 모듈 설치
- package.json 파일이 자동으로 업데이트 됨
  
```bash
yarn add [package]
yarn add [package]@[version]
yarn add [package]@[tag]
```
  
### 다른 범주의 의존성 모듈 설치
  
```bash
yarn add [package] --dev
yarn add [package] --peer
yarn add [package] --optional
```
  
### 의존성 모듈 업데이트
  
```bash
yarn upgrade [package]
yarn upgrade [package]@[version]
yarn upgrade [package]@[tag]
```
  
### 의존성 모듈 제거
  
```bash
yarn remove [package]
```

> **memo**
>
> yarn.lock 파일은 설치된 모듈의 버전을 저장해 어디서나 같은 버전과 구소의 의존성을 가지게 함. yarn.install 할때마다 yarn.lock 파일이 생성되며, package-lock.json 파일과 같은 역할을 함 
{: .notice--info}  

---
  
# 연결문서
