---
title : "useEffect"
excerpt : "useEffect"
toc : true
toc_sticky : true
toc_label : "useEffect"
categories:
- ReactStudy
tags:
- [React, Study]
last_modified_at: 2024-08-21T08:00:00-10:00:00
---
  
---
  
 이 글에서는 React 프로젝트에서 자주 등장하는 useEffect에 대해서 알아보겠다.

> **useEffect란?**  
>
> React의 주요 Hook 중 하나로, 컴포넌트가 렌더링 될 때와 관련된 부수효과를 처리하기 위해 사용된다. 
{: .notice--info}  

 예를 들어 데이터를 가져오거나, 구독 설정을 하거나, DOM을 직접 조작하거나 할 때, useEffect Hook을 사용한다.

 useEffect 는 React Componenet가 **렌더링 된 후**에 특정 작업을 수행하도록 설정한다. 

 사용 예제를 살펴보면,
  
```javascript
import { useEffect } from 'react';

function MyComponent() {
    useEffect(() => {
        // 이곳에 부수효과를 처리하는 코드를 작성합니다.
        console.log('컴포넌트가 렌더링되었습니다.');

        // 선택적으로 정리(clean-up) 함수를 반환할 수 있습니다.
        return () => {
            console.log('컴포넌트가 언마운트되거나 업데이트되기 직전에 실행됩니다.');
        };
    }, []); // 의존성 배열
}
```

 여기서 의존성 배열은 useEffect가 언제 실행될지 결정하는 중요한 요소이다. 
  
| 의존성 배열 데이터 | 역할                                    | 예시                  |
| ---------- | ------------------------------------- | ------------------- |
| 빈 배열       | Component가 처음 렌더링 되는 한번만 useEffect 실행 | []                  |
| 값이 있는 배열   | 배열 안에 있는 값이 변경 될 때마다 useEffect 실행     | [name, phoneNumber] |
| 배열 자체를 생략  | Component가 렌더링 될 때마다 useEffect 실행     |                     |

 몇가지 예제를 더 살펴보자.
  
```javascript
import React, { useState, useEffect } from 'react';

function DataFetchingComponent() {
    const [data, setData] = useState(null);

    useEffect(() => {
        fetch('https://api.example.com/data')
            .then(response => response.json())
            .then(data => setData(data))
            .catch(error => console.error('Error fetching data:', error));
    }, []); // 빈 배열로 의존성 설정: 한 번만 실행됨

    return (
        <div>
            {data ? <div>Data: {JSON.stringify(data)}</div> : <div>Loading...</div>}
        </div>
    );
}
```

 위 소스코드는 컴포넌트가 렌더링 된 후 Backend 서버의 API 를 호출하여 데이터를 받아오는 예제이다.
  
```javascript
import React, { useEffect } from 'react';

function ResizeComponent() {
    useEffect(() => {
        function handleResize() {
            console.log('Window resized');
        }

        window.addEventListener('resize', handleResize);

        // 정리 함수에서 이벤트 리스너를 제거
        return () => {
            window.removeEventListener('resize', handleResize);
        };
    }, []); // 빈 배열로 의존성 설정: 한 번만 실행되고, 컴포넌트가 언마운트될 때 정리됨

    return <div>Resize the window and check the console!</div>;
}
```

 위 예제는 컴포넌트가 렌더링 된 후 Event Listener를 처리하는 예시이다.
  
---
  
# 연결문서
