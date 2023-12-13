---
title : "Vue-LocalStorage"
excerpt : "Vue-LocalStorage"
toc : true
toc_sticky : true
toc_label : "Vue-LocalStorage"
categories:
- VueStudy
tags:
- [Vue, FrontEnd, Study]
last_modified_at: 2023-11-01T08:00:00-10:00:00
---

# 날짜 : 2023-11-01 18:05

# 태그 :  #Vue #FrontEnd #Study 
---

# 내용

## 사용하는 이유
- 페이지 새로 고침해도 데이터 유지
- 네트워크 요청시 서버로 전송되지 않음
- 여러 탭이나 창 간 데이터 공유 가능

## Vite 프로젝트에서 LocalStorage  사용

### pinia-plugin-persistedstate
- Pinia Local Storage 사용 Plugin

#### 설치

```bash
npm i pinia-plugin-persistedstate
```

#### import

```javascript
import piniaPluginPersistedstate from 'pinia-plugin-persistedstate'
```

#### 사용

##### app에 추가

```javascript
import { createApp } from 'vue'  
import { createPinia } from 'pinia'  
import piniaPluginPersistedstate from 'pinia-plugin-persistedstate'
  
import App from './App.vue'  
import router from './router'  
  
const app = createApp(App)  
  
const pinia = createPinia()  
pinia.use(piniaPluginPersistedstate)  
  
app.use(pinia)  
app.use(router)  
  
app.mount('#app')
```

##### Store의 3번째 인자 추가
- persist:true

```javascript
import {defineStore} from "pinia";  
  
export const useUserStore = defineStore('user', () =>{  
  ...
}, {persist:true})
```

---

# 연결문서
- [Vue-State](../../vuestudy/VueStudy-Vue-State)