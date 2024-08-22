---
title : "Tailwind"
excerpt : "Tailwind"
toc : true
toc_sticky : true
toc_label : "Tailwind"
categories:
- ReactStudy
tags:
- [React]
last_modified_at: 2024-08-20T08:00:00-10:00:00
---
  
---
  
## 환경 설정
 Tailwind 사용을 위해 먼저 npm을 사용해 설치한다.
  
```bash
npm install tailwindcss postcss autoprefixer
```

 그 다음으로 기본 설정파일을 생성한다.
  
```bash
npx tailwindcss init
```

 그러면 프로젝트 내에 tailwind.config.js 파일이 생성된다.

 vite 프로젝트의 경우 PostCSS를 사용하여 Tailwind CSS를 처리하므로 루트 디렉토리에 postcss.config.cjs 파일을 생성한 후 아래 내용을 저장한다.
  
```js
// postcss.config.cjs
module.exports = {
  plugins: {
    tailwindcss: {},
    autoprefixer: {},
  },
}
```

 그 다음은 tailwind.config.js 파일을 수정하여 Tailwind CSS의 기본 설정을 정의한다.
  
```js
// tailwind.config.js  
module.exports = {  
  content: [  
    "./src/**/*.{js,jsx}",  
  ],  
  theme: {  
    extend: {},  
  },  
  plugins: [],  
}
```

 위와 같이 purge 옵션을 사용하여 Tailwind CSS가 사용할 클래스만 포함하도록 설정한다.

 그리고 src/index.css 파일에 Tailwind 스타일을 포함시킨다.
  
```css
/* src/index.css */  
@tailwind base;  
@tailwind components;  
@tailwind utilities;
```
  
## 사용법
 이상으로 환경설정은 마쳤고, 이제 사용해보도록 하자.

 먼저 App.jsx에서 Tailwind를 사용해보자
  
```javascript
function App() {  
  return (  
    <>  
      <h1 className="text-2xl font-thin text-amber-500">Vite + React</h1>  
    </>  
  )  
}
```

 위와 같이 ClassName을 적용하여 Text의 폰트, 크기, 색상을 지정할 수 있다.

---
  
# 연결문서
- [Tailwind 공식문서](https://tailwindcss.com/docs/installation)