---
title : "VueAxios"
excerpt : "VueAxios"
toc : true
toc_sticky : true
toc_label : "VueAxios"
categories:
- VueStudy
tags:
- [Vue, FrontEnd, Study]
last_modified_at: 2023-11-01T08:00:00-10:00:00
---

# 날짜 : 2023-11-01 17:45

# 태그 : #Vue #FrontEnd #Study 
---

# 내용

## AXIOS

### 설치

```bash
npm install axios
```

## 객체 정의

### 방법 1

```javascript
import axios from "axios";  
  
export default axios.create({  
    baseURL: import.meta.env.VITE_URL,  
    headers:{  
        "Content-type" : "application/json"  
    }  
})
```

### 방법2

```javascript
import axios from 'axios';  
  
const instance = axios.create({  
    baseURL: import.meta.env.VITE_URL,  
    headers: {  
        "Content-Type":"application/json"  
    }  
})  
  
export default instance;
```

### logging

```javascript
instance.interceptors.request.use(  
    (config) => {  
        console.log('axios.js request : ' , config);  
        return config  
    },  
    (error) => {  
        return Promise.reject(error);  
    }  
);  
instance.interceptors.response.use(  
    (res) => {  
        console.log('axios.js response : ' , res);  
        return res  
    },  
    (error) => {  
        return Promise.reject(error);  
    }  
)  
```

## 사용

```javascript
import axios from "@/plugins/axios";  
import {useWelcomeMessageStore} from "@/stores/welcomeMessageStore"  
  
const message = useWelcomeMessageStore();  
  
const onClick = async()=> {  
  try{  
    await axios.get('/api/hello')  
        .then((response)=>{  
          console.log('data : ' + response.data)  
          message.setWelcomeMessage(response.data)  
        })  
  }catch(e){  
    console.log(e)  
    alert('Error데이터를 불러올 수 없습니다')  
  }  
}
```

---

# 연결문서
- [Vue-환경변수](../../vuestudy/vuestudy-Vue환경변수)
- [npm](../../nodejs/nodejs-npm)
- Api Sample :  https://dummyjson.com/docs/auth