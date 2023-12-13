---
title : "React-Syntax"
excerpt : "React-Syntax"
toc : true
toc_sticky : true
toc_label : "React-Syntax"
categories:
- ReactStudy
tags:
- [Javascript, Lecture, FrontEnd, React, Study]
last_modified_at: 2023-10-19T08:00:00-10:00:00
---

# 날짜 : 2023-10-19 16:13

# 태그 : #Javascript #Lecture #FrontEnd #React #Study 
---

# 내용

## Syntax

```javascript
export default function App(){
  const [message, setMessage] = useState("Hello");
  return (
    <>
      <p>message : {message}</p>
    </>
  )
}
```

### Template Literals
-  문자 안에 변수 사용하여 string 생성

```javascript
const myName = "david"
console.log(`이름은 ${myName} 입니다`);
```
  
![image](../../assets/images/TemplateLiteralResult.png)

### map
- function을 매개변수로 받아 Collection의 매개변수가 함수에 적용된 Collection 반환

```javascript 
const ages = [30,40,5];
const newAges = ages.map((age) => age + 1);

console.log(ages);
console.log(newAges);
```
  
![image](../../assets/images/LamdaResult.png)

### filter
- 함수에서 true를 리턴하는 Element만 배열로 반환

```javascript
const infos = [
  { name: "김창수", age: 30, family: ["할머니", "아내", "아들"] },

  { name: "이민주", age: 24, family: ["남편"] },

  { name: "박종식", age: 58, family: ["아들", "딸", "손자"] },
];

infos.filter((person) => {
	 return person.age > 25);
	});
```
  
![image](../../assets/images/LamdaResult%201.png)

### Clone
* \[...변수명\] 형식으로 clone 후 set 해야함.

```javascript
  function copySubTitle() {
    //clone
    let copy = [...goodCount];
  }
```

### 조건문

#### if else

```javascript
export default function App() {
  const [isActive, setIsActive] = useState(false);

  let content;

  if(isActive){
    content = <div>짠</div>;
  }
  else{
    content = <div>안보임</div>;
  }

  return (
    <>
      <button onClick={() => setIsActive(!isActive)}>토글 버튼</button>
      {content}
    </>
  );
}
```

#### 3항연산자

```javascript
export default function App() {
  const [isActive, setIsActive] = useState(false);

  return (
    <>
      <button onClick={() => setIsActive(!isActive)}>토글 버튼</button>
      {isActive ? <div>짠</div> : <div>안보임</div>}
    </>
  );
}
```

#### &&
- true일 경우만 보여줌
- AND 조건이라고 생각하자.
- 조건문이 boolean 이어야한다.

``` javascript
export default function App() {
  const [isActive, setIsActive] = useState(false);

  return (
    <>
      <button onClick={() => setIsActive(!isActive)}>토글 버튼</button>
      {isActive && <div>짠</div>}
    </>
  );
}
```

---

# 연결문서
