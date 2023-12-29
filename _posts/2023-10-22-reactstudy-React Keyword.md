---
title : "React Keyword"
excerpt : "React Keyword"
toc : true
toc_sticky : true
toc_label : "React Keyword"
categories:
- ReactStudy
tags:
- [React, FrontEnd, Syntax, Study]
last_modified_at: 2023-10-22T08:00:00-10:00:00
---

# 날짜 : 2023-10-22 20:04

# 태그 : #React #FrontEnd #Syntax #Study 
---

# 내용

## Syntax

### export default
- 현재 파일에서 export할 함수 지정

### tag keyword

#### className
- html의 class와 동일한 키워드
- javascript에서 class와 구분을 위해 키워드 변경됨

#### **useState**
- 리액트는 setter 호출시, 값의 참조 주소가 같으면 update 하지 않기 때문에 useState를 사용한다.
- 상태 생성시 사용
- 변경이 될 여지가 있는 데이터만 State로 선언
- 상태가 변하면 화면에서 해당 부분을 다시 렌더링
- **setter는 로직이 한번 동작해야 값이 갱신된다.**
- import

```javascript
import { useState } from "react";
```

- 선언 및 초기화 : useState(<초기값>) -> 하나의 배열을 리턴받음

```javascript
const [message, setMessage] = useState("Hello"); //선언 및 초기값 지정
```

- 값 사용

```javascript
<span>{message}</span>
```

- 값 변경

```javascript
setMeesage("변경할값");
```

#### useEffect

##### useEffect:mounted
- import

```javascript
import { useEffect } from "react";
```

- 사용

```javascript
  useEffect( () =>{
    async function dataFetch() {
      try {
        const response = await axios.get(URL);
        setUsers(response.data);
      } catch (error) {
        console.log(error);
      }
      console.log("요청 보냄");
    }
  
    dataFetch();
  }
  ,[]) // 두번째 파라미터 빈 배열
```

---

# 연결문서
- [React-LifeCycle](../../reactstudy/reactstudy-React-LifeCycle)