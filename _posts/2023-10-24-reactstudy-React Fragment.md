---
title : "React Fragment"
excerpt : "React Fragment"
toc : true
toc_sticky : true
toc_label : "React Fragment"
categories:
- ReactStudy
tags:
- [React, FrontEnd, Study]
last_modified_at: 2023-10-24T08:00:00-10:00:00
---
  
---
  
 React에서 자주 등장하는 Fragment에 대해서 알아보자.

> **Fragment란?**  
>
> React 에서 여러 Node를 하나로 그룹화 할 때 사용하는 Empty Node를 의미한다. 
{: .notice--info}  

 기본적으로 Fragment는 아래와 같이 생겼다.
  
```javascript
<>
</>
```

 Node들을 그룹화 할때, div 태그를 사용하면 되는것 아니야? 라고 생각하는 독자가 있을 것이다. 우리는 Fragment를 사용함으로서 **불필요한 DOM node 생성을 막을 수 있다**. 뿐만 아니라 **원하는 레이아웃을 유지**하면서 **여러 엘리먼트를 그룹화** 할 수 있다.

---
  
# 연결문서
