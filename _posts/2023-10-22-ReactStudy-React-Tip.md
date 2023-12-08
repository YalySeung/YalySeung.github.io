---
title : "React-Tip"
excerpt : "React-Tip"
toc : true
toc_sticky : true
toc_label : "React-Tip"
categories:
- ReactStudy
tags:
- [React, FrontEnd, Study]
last_modified_at: 2023-10-22T08:00:00-10:00:00
---

# 날짜 : 2023-10-22 21:02

# 태그 : #React #FrontEnd #Study 
---

# 내용

## 리스트 렌더링
- 태그 반복시, map, filter 사용
- key 값은 필수
- 2개 이상의 Element를 리스팅하려면 [React-Fragment](../../ReactStudy/ReactStudy-React-Fragment)를 사용한다.

```javascript
export default function App() {
  const [hideCompleted, setHideCompleted] = useState(false);
  const todos = [
    { id: 1, text: "HTML 배우기", done: true },
    { id: 2, text: "JavaScript 배우기", done: true },
    { id: 3, text: "React 배우기", done: false },
  ];
  return (
    <>
      <ul>
        {todos
          .filter((todo) => {
            console.log(hideCompleted);
            if (hideCompleted) return todo.done;
            else return todo;
          })
          .map((todo) => (
            <li key={todo.id}>
              <span>{todo.text}</span>
            </li>
          ))}
      </ul>
      <button onClick={() => setHideCompleted(!hideCompleted)}>토글</button>
    </>
  );
}
```

---

# 연결문서
