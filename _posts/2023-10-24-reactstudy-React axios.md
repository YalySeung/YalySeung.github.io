---
title : "React axios"
excerpt : "React axios"
toc : true
toc_sticky : true
toc_label : "React axios"
categories:
- ReactStudy
tags:
- [React, FrontEnd, Study]
last_modified_at: 2023-10-24T08:00:00-10:00:00
---

# 날짜 : 2023-10-24 13:37

# 태그 : #React #FrontEnd #Study 
---

# 내용

## 정의
> **axios 란**
>
> 브라우저를 위한 Promise 기반 HTTP 클라이언트
{: .notice--info}

## 설치

```ruby
npm i axios
```
  
![image](../../assets/images/InstallAxiosResult.png)

## 사용하기

### import 

```javascript
import axios from "axios";
```

### target URL 설정

```javascript
const URL = "https://jsonplaceholder.typicode.com/todos";
```

### async await 사용

```javascript
  <button
	onClick={async () => {
	  try{
		const response = await axios.get(URL);
		setData(response.data);
	  }
	  catch (error){
		console.error(error);
	  }
	  
	}}
>
{: .notice--info}
	데이터패치
  </button>
```

---

# 연결문서
- [Javascript](../../프로그래밍언어/프로그래밍언어-Javascript#async-await)