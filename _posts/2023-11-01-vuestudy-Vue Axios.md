---
title : "Vue Axios"
excerpt : "Vue Axios"
toc : true
toc_sticky : true
toc_label : "Vue Axios"
categories:
- VueStudy
tags:
- [Vue, FrontEnd, Study]
last_modified_at: 2023-11-01T08:00:00-10:00:00
---
  
---
  
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
{: .notice}  
        console.log('axios.js request : ' , config);  
        return config  
    },  
    (error) => {   
{: .notice}  
        return Promise.reject(error);  
    }  
);  
instance.interceptors.response.use(  
    (res) => {   
{: .notice}  
        console.log('axios.js response : ' , res);  
        return res  
    },  
    (error) => {   
{: .notice}  
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
{: .notice}  
  try{  
    await axios.get('/api/hello')  
        .then((response)=>{   
{: .notice}  
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
- [Vue-환경변수](../../vuestudy/vuestudy-Vue-환경변수)
- [npm](../../nodejs/nodejs-npm)
- Api Sample :  https://dummyjson.com/docs/auth