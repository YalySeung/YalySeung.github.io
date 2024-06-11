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
  
##  컴포넌트
- 하나의 UI를 의미(버튼, 이미지, Grid 등등)
- PascalCase로 작성
- **컴포넌트 내 로직은 컴포넌트에 변경이 있을 때 마다 호출된다.**
  
```javascript
export default function App() {
  const [weight, setWeight] = useState(0);
  const [height, setHeight] = useState(0);
  let content;
  let bmi;

  if (weight === 0) content = <div>계산불가</div>; 
{: .notice}  
  else if (height === 0) content = <div>계산불가</div>; 
{: .notice}  

  bmi = weight / (0.01 * 0.01 * height * height);

  if (bmi < 18.5) content = <div>저체중</div>; 
{: .notice}  
  else if (bmi >= 18.5 && bmi < 25) content = <div>정상</div>; 
{: .notice}  
  else content = <div>과체중</div>; 
{: .notice}  

  return (
    <> 
{: .notice}  
      <h1>BMI 계산기</h1> 
{: .notice}  
      <div> 
{: .notice}  
        <label> 
{: .notice}  
          신장
          <input
            type="number"
            onChange={(e) => { 
{: .notice}  
              setHeight(e.target.value);
            }}
          /> 
{: .notice}  
        </label> 
{: .notice}  
      </div> 
{: .notice}  
      <div> 
{: .notice}  
        <label> 
{: .notice}  
          체중
          <input
            type="number"
            onChange={(e) => { 
{: .notice}  
              setWeight(e.target.value);
            }}
          /> 
{: .notice}  
        </label> 
{: .notice}  
      </div> 
{: .notice}  
      {content}
    </> 
{: .notice}  
  );
}
```
  
### 컴포넌트 분리의 장단점
  
#### 장점
- html 페이지의 Item을 각각 파일로 구분하여 유지보수가 용이
  
#### 단점
- 분리된 컴포넌트간 데이터 연동 고려 필요
- 부모 컴포넌트가 자식 컴포넌트에 데이터 전달 방법 필요
  
### 컴포넌트 추가
  
#### components 폴더 하위에 jsx 생성
  
![image](../../assets/images/AppHeaderjsx.png)
  
#### jsx 파일 작성
  
```javascript
export default function AppFooter(){
    return (
        <> 
{: .notice}  
            <h2>AppFooter</h2> 
{: .notice}  
        </> 
{: .notice}  
    )
}
```
  
#### App.Jsx에 import 후 컴포넌트 추가
  
```javascript
import AppFooter from "./components/AppFooter";

export default function App(){
  return (
    <> 
{: .notice}  
      <h1>App</h1> 
{: .notice}  
      <AppFooter/> 
{: .notice}  
    </> 
{: .notice}  
  );
}
```
  
---
  
# 연결문서
