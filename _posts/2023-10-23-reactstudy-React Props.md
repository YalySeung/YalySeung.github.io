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

# 날짜 : 2023-10-23 15:11

# 태그 : #React #FrontEnd #Study 
---

# 내용

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
```

- 자식 컴포넌트에서 사용

```javascript
export default function AppChild({ name, age })
```

#### useState
- setState 내리기

```javascript
<AppChild name={name} age={age} onChangeName={(newName) => setName(newName)}/>
```

- setState 받아 쓰기

```javascript
<button onClick={() => onChangeName("tom")} >이름 바꾸기</button>
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
      <h1>App</h1>
      <p>{name}</p>
      <p>{age}</p>
      <AppChild name={name} age={age}/>
    </>
  );
}
```

- 자식 컴포넌트에서 사용

```javascript
export default function AppChild({ name, age }) {
  return (
    <>
      <h2>AppChild</h2>
      <p>{name}</p>
      <p>{age}</p>
      <GrandChild />
    </>
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
      <h1>App</h1>
      <p>{title}</p>
      <p>{salt}</p>
      <FriedChicken title={title} salt={salt} onChangeSalt={(newSalt) => setSalt(newSalt)}/>
    </>
  );
}
```

- FriedChicken.jsx

```javascript
import ChickenChild from "./ChickenChild";

export default function FriedChicken({title, salt, onChangeSalt}){
  return (
    <>
      <h2>FriedChicken</h2>
      <p>{title}</p>
      <p>{salt}</p>
      <ChickenChild title={title} salt={salt} onChangeSalt={onChangeSalt}/>
    </>
  );
}
```

- ChickenChild.jsx

```javascript
export default function ChickenChild({title, salt, onChangeSalt}) {
  return (
    <>
      <h3>ChickenChild</h3>
      <p>{title}</p>
      <p>{salt}</p>
      <button onClick={() => onChangeSalt(20)}>소금을 줄이자</button>
    </>
  );
}
```

---

# 연결문서
- [React-Keyword](../../reactstudy/reactstudy-React-Keyword#usestate)