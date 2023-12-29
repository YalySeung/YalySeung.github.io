---
title : "Vue 환경변수"
excerpt : "Vue 환경변수"
toc : true
toc_sticky : true
toc_label : "Vue 환경변수"
categories:
- VueStudy
tags:
- [Vue, FrontEnd, Study]
last_modified_at: 2023-11-01T08:00:00-10:00:00
---

# 날짜 : 2023-11-01 17:55

# 태그 : #Vue #FrontEnd #Study 
---

# 내용

## 환경변수 사용 방법

### .env 파일 생성
  
![image](../../assets/images/VueENVFile.png)

### 사용
- 선언된 환경변수는 빌드시점에 **import.meta.env** 객체에 주입
- **환경변수명은 VITE로 시작해야한다.**

```javascript
onMounted(() => {  
  console.log(import.meta.env.VITE_TEST)  
})
```

### 주의사항
- vite.config.js 파일에서 환경 변수를 사용하려면, **전역 변수로 먼저 선언**해야한다.

```javascript
const {VITE_URL} = import.meta.env  
export default defineConfig({  
    server: {  
        proxy: {  
            '/api': {  
                target: VITE_URL,  
                ws: true,  
                changeOrigin: true  
            }  
        },
        ...
```

### vite 프로젝트에서 환경 변수 파일 별 사용처

|파일명|사용처|
|---|---|
|.env|모든 상황에서 사용될 환경변수|
|.env.\<mode\>|로컬 개발에서 사용할 환경변수|
|.env.local|특정 모드에서만 사용될 환경 변수|
|.env.\<mode\>.local|특정 모드에서만 사용되나, 로컬 개발 환경에서만 사용될 환경 변수|

---

# 연결문서
