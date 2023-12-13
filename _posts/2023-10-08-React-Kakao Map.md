---
title : "Kakao Map"
excerpt : "Kakao Map"
toc : true
toc_sticky : true
toc_label : "Kakao Map"
categories:
- React
tags:
- [React, ExternalAPI, Kakao]
last_modified_at: 2023-10-08T08:00:00-10:00:00
---

# 날짜 : 2023-10-08 13:31

# 태그 : #React #ExternalAPI #Kakao
---

# 내용

## index.html
- 스크립트 추가 : Kakao 라이브러리 import

```html
<script type="text/JavaScript" src="//dapi.kakao.com/v2/maps/sdk.js?appkey=0d58a7c4c5ed270a2c5b5ab2fbc4cb1a"></script>
```

## App.js

```java
import React, { useEffect } from 'react';

function Kakao() {
  useEffect(() => {
    const container =document.getElementById('map'); //지도를 담을 영역의 DOM 레퍼런스
    const options = {
      center : new kakao.maps.LatLng(33.450701, 126.570557), //지도의 중심좌표
      level : 3
    };

    const map = new kakao.maps.Map(container, options);// 지도 생성 및 객체 리턴
  }, {})
  
  return (
    <div
    id = "map"
    style={{width: "80%",
		    height: '500px',
		  }}>
	</div>
}

export default Kakao
```

---

# 연결문서
- [외부API 연동](../../react/React-외부API-연동)

