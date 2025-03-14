---
title : "React useCallback"
excerpt : "React useCallback"
toc : true
toc_sticky : true
toc_label : "React useCallback"
categories:
- ReactStudy
tags:
- [React]
last_modified_at: 2024-08-01T08:00:00-10:00:00
---
  
---
  
> **useCallback이란?**  
>
>  렌더링 간에 함수 정의를 캐싱해 주는 React Hook이다. 
{: .notice--info}  

  `useCallback`은 **컴포넌트가 리렌더링될 때 동일한 함수를 재사용하도록 도와주는 Hook**이다.  
  불필요한 함수 재생성을 방지하여 성능 최적화에 도움을 준다.
  
## 사용법
  
### 1️⃣ 기본적인 `useCallback` 사용 예제
  
```javascript
import React, { useState, useCallback } from "react";

const Counter = () => {
    const [count, setCount] = useState(0);

    const increment = useCallback(() => {
        setCount((prev) => prev + 1);
    }, []); // 빈 배열을 넣으면 컴포넌트가 처음 마운트될 때만 함수가 생성됨

    return (
        <div>
            <p>Count: {count}</p>
            <button onClick={increment}>Increment</button>
        </div>
    );
};

export default Counter;
```
  
### 2️⃣ `useCallback`을 `props`로 전달할 때 사용
  
```javascript
const Parent = () => {
    const [count, setCount] = useState(0);

    const increment = useCallback(() => {
        setCount((prev) => prev + 1);
    }, []);

    return <Child onIncrement={increment} />;
};

const Child = React.memo(({ onIncrement }) => {
    console.log("Child 렌더링");
    return <button onClick={onIncrement}>Increment</button>;
});
```
  
## `useCallback` vs `useMemo`
  
| Hook | 역할 | 사용 목적 |
|------|------|---------|
| `useCallback` | 함수 캐싱 | 함수 재생성 방지 |
| `useMemo` | 값 캐싱 | 연산 비용 절감 |
  
## 장점과 단점
  
### ✅ 장점
- **불필요한 함수 재생성을 방지**하여 성능 최적화
- **컴포넌트가 불필요하게 리렌더링되는 것을 줄일 수 있음**  
  
### ❌ 단점
- **잘못 사용하면 코드 복잡도가 증가**할 수 있음
- 모든 함수에 적용하는 것은 오히려 성능 저하를 초래할 수 있음

---
  
# 연결문서
