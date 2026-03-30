---
title : "Page Deploy"
excerpt : "Page Deploy"
toc : true
toc_sticky : true
toc_label : "Page Deploy"
categories:
- GithubBlog
tags:
- [Git, React, Frontend, portfolio]
last_modified_at: 2026-03-30T08:00:00-10:00:00
---
  
---
  
## 📌 GitHub Actions로 페이지 배포하기

> **info**
>
> GitHub Pages는 **정적 파일을 호스팅하는 서비스**이고, GitHub Actions는 **빌드와 배포 과정을 자동화하는 CI/CD 도구**이다. 
{: .notice--info}  

 React 또는 Vite 기반 포트폴리오 프로젝트는 **배포 스크립트와 GitHub Actions Workflow를 함께 구성**하면 매번 수동으로 build 결과물을 올리지 않아도 된다.

 이 문서에서는 **프로젝트에 배포 스크립트를 추가하고, GitHub Actions로 GitHub Pages에 배포하는 방식**을 일반화하여 정리한다.

---
  
## 📌 전체 흐름

 전체 배포 흐름은 다음과 같다.
  
```text
소스 수정
→ GitHub main 브랜치 push
→ GitHub Actions 실행
→ 프로젝트 build
→ 정적 파일 업로드
→ GitHub Pages 배포
```

 이 구조의 장점은 **로컬에서 build 결과물을 직접 커밋하지 않아도 된다는 점**이다.

---
  
## 📌 왜 GitHub Actions를 사용하는가

 GitHub Pages는 단순 정적 호스팅이지만, Actions를 함께 사용하면 다음과 같은 장점이 있다.

- 수동 배포 제거
- 브랜치 push만으로 자동 배포
- build / deploy 절차 표준화
- 협업 시 배포 방식 일관성 확보

 특히 포트폴리오처럼 **소스는 자주 수정되지만 배포는 간단해야 하는 프로젝트**에 적합하다.

---
  
## 📌 프로젝트 준비

 배포 대상이 React 또는 Vite 기반 정적 페이지라고 가정한다.

 기본적으로 다음 명령어로 build가 가능해야 한다.
  
```bash
npm install
npm run build
```

 Vite 기준으로는 보통 `dist` 디렉토리가 생성된다.
  
```text
dist/
```

 React(CRA) 기준으로는 보통 `build` 디렉토리가 생성된다.
  
```text
build/
```

 즉 GitHub Actions는 **이 build 결과 디렉토리를 GitHub Pages에 배포**하게 된다.

---
  
## 📌 package.json 스크립트 구성

 먼저 프로젝트에서 build 스크립트가 명확해야 한다.

 예시
  
```json
{
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "preview": "vite preview"
  }
}
```

 핵심은 **Actions가 `npm run build`만 실행해도 정적 파일이 생성되는 상태**를 만드는 것이다.

---
  
## 📌 GitHub Actions Workflow 추가

 GitHub Actions Workflow 파일은 보통 아래 위치에 둔다.
  
```text
.github/workflows/deploy.yml
```

 예시
  
```yaml
name: Deploy portfolio to GitHub Pages

on:
  push:
    branches:
      - main
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: "pages"
  cancel-in-progress: true

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Setup Node
        uses: actions/setup-node@v4
        with:
          node-version: 20
          cache: npm

      - name: Install dependencies
        run: npm ci

      - name: Build
        run: npm run build

      - name: Setup Pages
        uses: actions/configure-pages@v5

      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: ./dist

  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    needs: build

    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

 위 예시는 **Vite 기준으로 `dist` 디렉토리를 업로드**하는 구조이다.

 CRA 기반이라면 아래 부분을 수정하면 된다.
  
```yaml
path: ./build
```

---
  
## 📌 GitHub Pages 설정

 Repository에서 Pages 설정도 함께 맞춰야 한다.

 설정 위치
  
```text
Repository → Settings → Pages
```

 확인할 항목

- Source : GitHub Actions
- 배포 브랜치 직접 선택 방식이 아니라 **Actions 배포 방식**으로 전환

 즉 이 방식은 예전처럼 `gh-pages` 브랜치에 정적 파일을 직접 올리는 구조가 아니라,  
 **Workflow가 artifact를 업로드하고 Pages가 이를 배포**하는 구조이다.

---
  
## 📌 Vite 프로젝트에서 base 설정 주의

 GitHub Pages는 저장소 경로 기반으로 접근하는 경우가 많다.

 예를 들어 저장소명이 `portfolio` 라면 실제 접근 경로는 다음처럼 될 수 있다.
  
```text
https://username.github.io/portfolio/
```

 이 경우 Vite 설정에서 `base`를 맞춰야 한다.
  
```ts
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'

export default defineConfig({
  plugins: [react()],
  base: '/portfolio/'
})
```

 만약 사용자 페이지 저장소처럼 `username.github.io` 자체를 사용하는 경우에는 보통 `/` 를 사용할 수 있다.
  
```ts
base: '/'
```

 **이 설정이 맞지 않으면 CSS / JS 경로가 깨져서 배포 후 화면이 정상 표시되지 않는다.**

---
  
## 📌 React Router 사용 시 주의사항

 GitHub Pages는 정적 호스팅이기 때문에 브라우저 새로고침 시 라우팅 문제가 발생할 수 있다.

 대표적인 해결 방식

- `HashRouter` 사용
- 404 fallback 처리
- 단일 페이지 구조 유지

 예를 들어 GitHub Pages에서 간단하게 운영하려면 아래처럼 `HashRouter`를 사용할 수 있다.
  
```tsx
import { HashRouter } from 'react-router-dom'

function AppRouter() {
  return (
    <HashRouter>
      {/* routes */}
    </HashRouter>
  )
}
```

 프로젝트 구조에 따라 `BrowserRouter` + fallback 파일 전략을 쓸 수도 있지만,  
 GitHub Pages에서는 **HashRouter가 가장 단순하고 안정적**이다.

---
  
## 📌 이 방식의 장점
  
### ✅ 장점

- build 결과물 직접 커밋 불필요
- push만으로 자동 배포
- 배포 절차 재현 가능
- CI/CD 흐름 경험 정리 가능
- 포트폴리오 프로젝트에 적합
  
### ✅ 특히 좋은 점

 포트폴리오는 디자인이나 문구를 자주 수정하게 되는데,  
 GitHub Actions를 사용하면 **배포 자체를 신경 쓰지 않고 소스 수정에만 집중**할 수 있다.

---
  
## 📌 운영 시 확인할 항목

 배포가 안 될 때는 다음 항목을 확인한다.

- Workflow 실행 성공 여부
- `npm run build` 실패 여부
- Pages 설정이 `GitHub Actions` 로 되어 있는지
- Vite `base` 경로가 올바른지
- Router 설정이 GitHub Pages 환경에 맞는지

 즉 **배포 실패 원인은 코드 문제보다 경로 설정이나 Pages 설정 문제인 경우가 많다.**

---
  
## 📌 정리

 GitHub Pages 배포 방식은 크게 두 가지가 있다.

| 방식 | 설명 |
|-----|-----|
| build 결과물 직접 업로드 | 수동 배포 |
| GitHub Actions 배포 | 자동 배포 |

 포트폴리오 프로젝트에서는 **GitHub Actions 기반 자동 배포 방식이 유지보수성과 재현성 측면에서 더 적합하다.**

---
  
## 📌 결론

 React / Vite 기반 포트폴리오 프로젝트는 **배포 스크립트와 GitHub Actions Workflow를 함께 구성**하면 GitHub Pages에 안정적으로 자동 배포할 수 있다.

 이 방식은 단순히 페이지를 올리는 것을 넘어  
 **프론트엔드 프로젝트의 배포 자동화 경험을 정리할 수 있다는 점에서도 의미가 있다.**
  
# 연결 문서
- [Github Blog 만들기](../../githubblog/githubblog-Github-Blog-만들기)
- [Git-Bash CLI](../../git/git-Git-Bash-CLI)
