---
title : "React Router"
excerpt : "React Router"
toc : true
toc_sticky : true
toc_label : "React Router"
categories:
- ReactStudy
tags:
- [React]
last_modified_at: 2024-08-01T08:00:00-10:00:00
---
  
---
  
> **React Router란?**  
>
>  React 애플리케이션에서 클라이언트 사이드 라우팅을 구현하는 라이브러리이다. 
{: .notice--info}  

  React Router를 사용하면 **페이지 리로드 없이 URL 변경을 처리하여 부드러운 내비게이션 경험을 제공**할 수 있다.
  
## React Router 적용
  먼저 React Router 패키지를 설치한다.
  
```bash
npm install react-router-dom
```
  
### 1️⃣ 기본적인 `BrowserRouter` 설정
  
```javascript
import React from "react";
import { BrowserRouter as Router, Route, Routes } from "react-router-dom";
import Home from "./Home";
import About from "./About";

const App = () => {
    return (
        <Router>
            <Routes>
                <Route path="/" element={<Home />} />
                <Route path="/about" element={<About />} />
            </Routes>
        </Router>
    );
};

export default App;
```
  
### 2️⃣ `useNavigate`를 활용한 페이지 이동
  
```javascript
import { useNavigate } from "react-router-dom";

const Home = () => {
    const navigate = useNavigate();

    return (
        <div>
            <h1>Home Page</h1>
            <button onClick={() => navigate("/about")}>Go to About</button>
        </div>
    );
};
```
  
## 장점과 단점
  
### ✅ 장점
- **페이지 리로드 없이** 부드러운 내비게이션 가능
- SPA에서 **효율적인 경로 관리 제공**  
  
### ❌ 단점
- 초기 설정이 필요하며, 동적 라우팅 구현이 복잡할 수 있음
- SEO 최적화가 어렵고, 서버 사이드 렌더링(SSR)과 함께 사용할 경우 추가 설정 필요  

---
  
# 연결문서