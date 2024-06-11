---
title : "React Props"
excerpt : "React Props"
toc : true
toc_sticky : true
toc_label : "React Props"
categories:
- ReactStudy
tags:
- [React, FrontEnd, Study]
last_modified_at: 2023-10-23T08:00:00-10:00:00
---
  
---
  
## Props
  
### 필요성
- 하나의 화면에서 상태 중복 발생
  
### 역할
- 상태를 위로 끌어올리기
- 필요할때 자식에게 내려보내기
  
### 사용법
- 자식 컴포넌트에 전달
  
```javascript
<AppChild name={name} age={age}/> 
{: .notice}  
```  
- 자식 컴포넌트에서 사용
  
```javascript
export default function AppChild({ name, age })
```
  
#### useState
- setState 내리기
  
```javascript
<AppChild name={name} age={age} onChangeName={(newName) => setName(newName)}/> 
{: .notice}  
```  
- setState 받아 쓰기
  
```javascript
<button onClick={() => onChangeName("tom")} >이름 바꾸기</button> 
{: .notice}  
```
  
### 예시
  
#### 이름 나이 예제
- 자식 컴포넌트에 전달
  
```javascript
export default function App(){
  const [name, setName] = useState("david");
  const [age, setAge] = useState(15);

  return (
    <> 
{: .notice}  
      <h1>App</h1> 
{: .notice}  
      <p>{name}</p> 
{: .notice}  
      <p>{age}</p> 
{: .notice}  
      <AppChild name={name} age={age}/> 
{: .notice}  
    </> 
{: .notice}  
  );
}
```  
- 자식 컴포넌트에서 사용
  
```javascript
export default function AppChild({ name, age }) {
  return (
    <> 
{: .notice}  
      <h2>AppChild</h2> 
{: .notice}  
      <p>{name}</p> 
{: .notice}  
      <p>{age}</p> 
{: .notice}  
      <GrandChild /> 
{: .notice}  
    </> 
{: .notice}  
  );
}
```
  
#### 치킨 소금 예제
- App.jsx
  
```javascript
import FriedChicken from "./components/FriedChicken";

export default function App(){
  const [title, setTitle] = useState("치킨은 맛있다.");
  const [salt, setSalt] = useState(30);

  return (
    <> 
{: .notice}  
      <h1>App</h1> 
{: .notice}  
      <p>{title}</p> 
{: .notice}  
      <p>{salt}</p> 
{: .notice}  
      <FriedChicken title={title} salt={salt} onChangeSalt={(newSalt) => setSalt(newSalt)}/> 
{: .notice}  
    </> 
{: .notice}  
  );
}
```  
- FriedChicken.jsx
  
```javascript
import ChickenChild from "./ChickenChild";

export default function FriedChicken({title, salt, onChangeSalt}){
  return (
    <> 
{: .notice}  
      <h2>FriedChicken</h2> 
{: .notice}  
      <p>{title}</p> 
{: .notice}  
      <p>{salt}</p> 
{: .notice}  
      <ChickenChild title={title} salt={salt} onChangeSalt={onChangeSalt}/> 
{: .notice}  
    </> 
{: .notice}  
  );
}
```  
- ChickenChild.jsx
  
```javascript
export default function ChickenChild({title, salt, onChangeSalt}) {
  return (
    <> 
{: .notice}  
      <h3>ChickenChild</h3> 
{: .notice}  
      <p>{title}</p> 
{: .notice}  
      <p>{salt}</p> 
{: .notice}  
      <button onClick={() => onChangeSalt(20)}>소금을 줄이자</button> 
{: .notice}  
    </> 
{: .notice}  
  );
}
```  
---
  
# 연결문서
- [React-Keyword](../../reactstudy/reactstudy-React-Keyword#usestate)