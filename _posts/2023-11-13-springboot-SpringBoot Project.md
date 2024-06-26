---
title : "SpringBoot Project"
excerpt : "SpringBoot Project"
toc : true
toc_sticky : true
toc_label : "SpringBoot Project"
categories:
- SpringBoot
tags:
- [SpringBoot]
last_modified_at: 2023-11-13T08:00:00-10:00:00
---
  
---
  
## SpringBoot 프로젝트 구성
  
![image](../../assets/images/SpringVueProjectStructure.png)
  
## 필요 외부 모듈
  
### axios
- api 서비스 비동기 호출
  
```bash
npm install axios
```
  
### path
- vue.config.js에서 빌드된 결과물의 타겟 디렉토리를 설정
  
```bash
npm install path
```
  
## Vue.js dev 서버에 proxy 설정
- Boot 서버 포트 변경
- vite.config.js
  
```javascript
import {fileURLToPath, URL} from 'node:url'  
  
import {defineConfig} from 'vite'  
import vue from '@vitejs/plugin-vue'  
  
// https://vitejs.dev/config/  
const {VITE_URL} = import.meta.env  
export default defineConfig({  
    server: {  
        proxy: {  
            '/api': {  
                target: VITE_URL,  
                ws: true,  
                changeOrigin: true  
            }  
        }
    },  
    plugins: [  
        vue(),  
    ],  
    resolve: {  
        alias: {  
            '@': fileURLToPath(new URL('./src', import.meta.url))  
        }  
    }  
})
```

---
  
# 연결문서
- [Intellij](../../ide/ide-Intellij)
- [Vue-프로젝트-Init](../../vuestudy/vuestudy-Vue-프로젝트-Init)
- [Vue-환경변수](../../vuestudy/vuestudy-Vue-환경변수)
- [npm](../../nodejs/nodejs-npm)