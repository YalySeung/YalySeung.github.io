---
title : "CustomComponent"
excerpt : "CustomComponent"
toc : true
toc_sticky : true
toc_label : "CustomComponent"
categories:
- React
tags:
- [React, Component]
last_modified_at: 2023-09-18T08:00:00-10:00:00
---

# 날짜 : 2023-09-18 22:57

# 태그 : #React #Component
---

# 내용

## 소스코드
- App.js

```javascript
import './App.css';
import { useState } from 'react';

function App() {
  let [subTitle, b] = useState([
    '여자 코드 추천',
    '남자 코트 추천',
    '남자 야구잠바 추천',
  ]);

  function copySubTitle() {
    //clone
    let copy = [...subTitle];
  }

  return (
    <div className="App">
      <ListItem subtitle={subTitle[0]} datestr="2월 17일 발행"></ListItem>
      <ListItem subtitle={subTitle[1]} datestr="2월 17일 발행"></ListItem>
      <ListItem subtitle={subTitle[2]} datestr="2월 17일 발행"></ListItem>
    </div>
  );
}

function ListItem(props) {
  return (
    <div className="list-item">
      <h4>{props.subtitle}</h4>
      <p>{props.datestr}</p>
    </div>
  );
}
```
* App.css

```javascript
div {
  box-sizing: border-box;
}
.list-item {
  padding-left: 20px;
  text-align: left;
  border-bottom: 1px solid grey;
}
```

---

# 연결문서

