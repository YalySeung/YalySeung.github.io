---
title : "vscode"
excerpt : "vscode"
toc : true
toc_sticky : true
toc_label : "vscode"
categories:
- IDE
tags:
- [IDE]
last_modified_at: 2024-11-26T08:00:00-10:00:00
---
  
---
  
> **Visual Studio Code란?**  
>
>  Microsoft에서 개발한 경량화된 코드 편집기로, 다양한 프로그래밍 언어를 지원하며 강력한 확장 기능을 제공한다. 
{: .notice--info}  

  VSCode는 **빠른 속도, 강력한 확장성, Git 통합 기능을 갖춘 오픈소스 코드 편집기**로, 개발자들이 선호하는 환경 중 하나이다.  
  
## 📌 VSCode 설치 방법
  
### 1️⃣ 공식 웹사이트에서 다운로드
- [VSCode 공식 사이트](https://code.visualstudio.com/)에서 운영체제에 맞는 설치 파일을 다운로드한다.
  
### 2️⃣ 터미널을 이용한 설치 (Mac & Linux)
  
```sh
  
# Mac (Homebrew 사용)
brew install --cask visual-studio-code
  
# Ubuntu (Snap 사용)
sudo snap install --classic code
```
  
## 📌 기본 사용법
  
### 3️⃣ 주요 단축키
  
| 기능                 | 단축키 (Windows/Linux) | 단축키 (Mac) |
| -------------------- | --------------------- | ------------ |
| 새 파일 생성         | `Ctrl + N`            | `Cmd + N`    |
| 파일 열기            | `Ctrl + O`            | `Cmd + O`    |
| 프로젝트 열기        | `Ctrl + K + O`        | `Cmd + K + O` |
| 터미널 열기          | `Ctrl + ~`            | `Cmd + ~`    |
| 검색 창 열기         | `Ctrl + Shift + F`    | `Cmd + Shift + F` |
| 설정 창 열기         | `Ctrl + ,`            | `Cmd + ,`    |
| 코드 포맷팅         | `Shift + Alt + F`     | `Shift + Option + F` |
| 코드 실행            | `Ctrl + Shift + B`    | `Cmd + Shift + B` |
| Git 변경 사항 보기   | `Ctrl + Shift + G`    | `Cmd + Shift + G` |
| 확장 프로그램 창 열기 | `Ctrl + Shift + X`    | `Cmd + Shift + X` |
  
### 4️⃣ 파일 탐색기에서 VSCode 실행
  
```sh
  
# 현재 디렉토리를 VSCode에서 열기
code .
```
  
## 📌 React 개발을 위한 확장 프로그램

| 확장                                           | 기능                                        |
| -------------------------------------------- | ----------------------------------------- |
| ES7 React/Redux/React-Native/JS snippets     | React와 Redux를 위한 코드 스니펫을 제공               |
| Prettier                                     | 코드 자동 정렬 및 형식화                            |
| ESLint                                       | 코드의 문법 및 스타일을 검사하고 오류를 표시                 |
| Live Server                                  | 저장할 때마다 브라우저가 자동으로 새로고침                   |
| Auto Rename Tag                              | HTML 태그를 수정할 때, 시작 및 종료 태그를 자동으로 함께 수정    |
| Path Intellisense                            | 파일 경로를 자동으로 완성                            |
| JavaScript (ES6) code snippets               | 최신 JavaScript 기능에 대한 코드 스니펫               |
| Stylelint                                    | CSS와 SCSS 코드에 대한 스타일 검사 및 오류 표시           |
| GitLens — Supercharge Git in VS Code       | Git 히스토리와 블레임 기능을 제공                      |
| Color Highlight                              | CSS 및 스타일링 파일에서 색상 코드를 강조표시               |
| npm Intellisense                             | `package.json` 파일을 편집할 때 npm 모듈 이름을 자동 완성 |
| Visual Studio Code CSS Intellisense for HTML | JSX 파일에서 CSS 클래스 이름 자동 완성 기능 제공           |
  
## 📌 VSCode에서 Git 사용법
  
### 5️⃣ VSCode에서 Git을 사용하려면?
- **Git이 설치되어 있어야 한다.**  
  
```sh
  git --version
  ```

- **Git 초기화 및 커밋**
  
```sh
  git init
  git add .
  git commit -m "첫 커밋"
  ```

- **GitHub 원격 저장소 연결**
  
```sh
  git remote add origin https://github.com/사용자명/저장소명.git
  git push -u origin main
  ```

- **VSCode의 Git UI 활용**
  1. `Ctrl + Shift + G` (`Cmd + Shift + G` - Mac)를 눌러 Git 창 열기
  2. 변경 사항을 선택 후 `Commit` 버튼 클릭
  3. `Push` 버튼을 눌러 원격 저장소로 업로드

---
  
# 연결문서
