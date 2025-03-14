---
title : "React Component"
excerpt : "React Component"
toc : true
toc_sticky : true
toc_label : "React Component"
categories:
- ReactStudy
tags:
- [React, FrontEnd, Study]
last_modified_at: 2023-10-23T08:00:00-10:00:00
---
  
---
  
 이 글에서는 React Component 에 대해서 알아볼 것이다.

> **React Component란?**  
>
> 버튼, 이미지, Grid 등의 하나의 UI를 의미한다. 
{: .notice--info}  

 Component는 PascalCase로 작성하며, 컴포넌트의 **function 내의 로직은 컴포넌트에변경이 있을 때마다 호출**된다.

 Component를 정의한 하나의 예시를 살펴보자.
  
```javascript
export default function App() {
  const [weight, setWeight] = useState(0);
  const [height, setHeight] = useState(0);
  let content;
  let bmi;

  if (weight === 0) content = <div>계산불가</div>;
  else if (height === 0) content = <div>계산불가</div>;

  bmi = weight / (0.01 * 0.01 * height * height);

  if (bmi < 18.5) content = <div>저체중</div>;
  else if (bmi >= 18.5 && bmi < 25) content = <div>정상</div>;
  else content = <div>과체중</div>;

  return (
    <>
      <h1>BMI 계산기</h1>
      <div>
        <label>
          신장
          <input
            type="number"
            onChange={(e) => {
              setHeight(e.target.value);
            }}
          />
        </label>
      </div>
      <div>
        <label>
          체중
          <input
            type="number"
            onChange={(e) => {
              setWeight(e.target.value);
            }}
          />
        </label>
      </div>
      {content}
    </>
  );
}
```

 이런 Component는 UI 의 요소 **각각을 파일로 구분하여 유지보수가 용이하다**는 장점이 있다. 반면 **분리된 컴포넌트간 데이터 연동을 고려**해야 하며 구조를 잘못 잡으면 오히려 소스코드가 복잡해 질 수 있다.
  
# Component 추가
 react 프로젝트에 신규 Component를 추가하는 방법을 살펴보자. 

 먼저 components 폴더 하위에 jsx 파일을 생헌다.
  
![image](../../assets/images/AppHeaderjsx.png)

 fotter 컴포넌트를 작성해보자.
  
```javascript
export default function AppFooter(){
    return (
        <>
            <h2>AppFooter</h2>
        </>
    )
}
```

 이제 App.jsx에 Footer 를 import 하자.
  
```javascript
import AppFooter from "./components/AppFooter";

export default function App(){
  return (
    <>
      <h1>App</h1>
      <AppFooter/>
    </>
  );
}
```

 독자들이 추가한 아름다운 Footer Component를 확인 가능하다.

---
  
# 연결문서
