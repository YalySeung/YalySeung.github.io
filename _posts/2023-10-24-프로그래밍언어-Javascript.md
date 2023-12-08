---
title : "Javascript"
excerpt : "Javascript"
toc : true
toc_sticky : true
toc_label : "Javascript"
categories:
- 프로그래밍언어
tags:
- [프로그래밍언어]
last_modified_at: 2023-10-24T08:00:00-10:00:00
---

# 날짜 : 2023-10-24 14:01

# 태그 : #프로그래밍언어
---

# 내용

## async await

### async
- 비동기 함수의 시작을 명시하는 키워드

### await
- 함수의 종료까지 line 실행을 기다리는 키워드

### 사용법

```javascript
  <button
	onClick={async () => {
	  try{
		const response = await axios.get(URL);
		setData(response.data);
	  }
	  catch (error){
		console.error(error);
	  }
	  
	}}
>

	데이터패치
  </button>

```

---

# 연결문서
