---
title : "ES Modules"
excerpt : "ES Modules"
toc : true
toc_sticky : true
toc_label : "ES Modules"
categories:
- DevelopCommon
tags:
- [DevelopCommon]
last_modified_at: 2024-08-21T08:00:00-10:00:00
---
  
---
  
 이 글에서는 **ES Modules**이 무엇인가에 대해서 알아보겠다.

> **ES Modules 이란?**  
>
> ECMAScript Modules 의 약어로 JavaScript의 모듈 시스템을 의미하며, ES6(ECMAscript 2015) 부터 도입되었다. 
{: .notice--info}  

 이 시스템은 Javascript 코드의 재사용성과 유지보수성을 높이기 위해 **파일 단위로 코드를 분리**하고, **필요한 부분만 가져와 사용하는 방식**을 제공한다.

 ES 모듈은 모듈 단위로 코드를 분리한다. Javascript 코드를 여러 파일로 분리하고, 각 파일을 하나의 모듈로 간주한다. 이렇게 하면 **각 모듈은 자신만의 스코프**를 가지며, 다른 모듈과의 충돌을 피할 수 있다. 

 ES 모듈은 모듈에서 함수, 변수, 클래스 등을  다른 모듈에서 사용할 수 있도록 **export** 키워드를 사용하여 내보낼 수 있다. 
  
```java
// math.js
export function add(x, y) {
    return x + y;
}

export const PI = 3.14159;
```

 이렇게 export 된 값은 다른 모듈에서 **import** 키워드로 가져와서 사용할 수 있다.
  
```java
// main.js
import { add, PI } from './math.js';

console.log(add(2, 3));  // 5
console.log(PI);  // 3.14159
```

 추가로 **export default** 키워드를 사용하면, 하나의 값을 기본으로 내보낼 수 있다. 이 경우 중괄호 없이 가져올 수 있다.
  
```java
// math.js
export default function multiply(x, y) {
    return x * y;
}

// main.js
import multiply from './math.js';

console.log(multiply(2, 3));  // 6
```

 ES 모듈은 정적으로 분석되기 때문에 import 와 export 파일의 최상위에서만 사용할 수 있으며, **조건문이나 함수 내부에서 사용할 수 없다**. 이 특성은 도구가 더 효율적으로 코드를 최적화 할 수 있도록 돕는다.

 한편, 브라우저 환경에서는 import() 함수를 사용하여 **모듈을 비동기로 로드**할 수 있다. 그래서 필요할 때문 모듈을 로드할 수 있게 하여 성능을 향상 시킬 수 있다.
  
```java
import('./math.js').then(math => { 
{: .notice--info}  
    console.log(math.add(2, 3));  // 5
});
```

 위 방법 뿐 아니라 대부분의 브라우저와 Node.js 에서 ES 모듈을 기본적으로 지원하기 때문에 script 태그를 이용하여 모듈을 로드 할 수 있다.
  
```java
<script type="module" src="main.js"></script> 
{: .notice}  
```

> **caution**
>
> Node.js 에서는 파일 확장자가 .mjs 이거나 package.json 에 type:module 로 설정하여 ES 모듈을 인식한다. 
{: .notice}  

---
  
# 연결문서
