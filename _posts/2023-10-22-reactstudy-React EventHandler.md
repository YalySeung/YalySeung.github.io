---
title : "React EventHandler"
excerpt : "React EventHandler"
toc : true
toc_sticky : true
toc_label : "React EventHandler"
categories:
- ReactStudy
tags:
- [React, FrontEnd, Study]
last_modified_at: 2023-10-22T08:00:00-10:00:00
---

# 날짜 : 2023-10-22 19:50

# 태그 : #React #FrontEnd #Study 
---

# 내용

## Event Handler
- 이벤트 명에 on 을 붙여 사용
- 함수 선언시, Component 안에 선언한다.

```javascript
export default function App(){
	//Componenet 영역
}
```

### Event Argument
- event 값에 매개변수를 입력해주면 이벤트 객체가 매개변수로 전달됨
- **e.target.value** 값 주로 사용

```javascript
<input type="text" value={message} onChange={(e) => setMessage(e.target.value)} />
```

### Event 종류

#### Click
- onClick
- **값으로 function을 사용한다**
- 클릭 이벤트 발생시, 함수 실행됨

```javascript
  <button onClick={() => {setText("짜잔");}}>클릭</button>
```

#### Change
- onChange
- input 태그에 많이 사용되는 방식

```javascript
<input
	type="text"
	placeholder="패스워드"
	value={password}
	onChange={(e) => setPassword(e.target.value)}
/>
```

---

# 연결문서
