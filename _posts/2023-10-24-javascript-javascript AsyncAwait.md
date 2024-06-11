---
title : "javascript AsyncAwait"
excerpt : "javascript AsyncAwait"
toc : true
toc_sticky : true
toc_label : "javascript AsyncAwait"
categories:
- javascript
tags:
- [프로그래밍언어, java]
last_modified_at: 2023-10-24T08:00:00-10:00:00
---
  
---
  
 async await는 **비동기 프로그래밍**에 사용되는 keyword이다. javascript에서 사용법을 설명하겠지만, 다른 프로그래밍 언어에서도 사용하는 방식은 크게 차이가 없다는 점을 참고했으면 한다.

 async는 **비동기 함수의 시작**을 명시하고, await는 **함수가 종료될 때까지 기다리겠다**고 명시한다. 간단한 예제 코드를 살펴보자
  
```javascript
  <button
	onClick={async () => { 
{: .notice}  
	  try{
		const response = await axios.get(URL);
		setData(response.data);
	  }
	  catch (error){
		console.error(error);
	  }
	  
	}}
> 
{: .notice}  
	데이터패치
  </button> 
{: .notice}  

```

 위 코드의 무명 async 함수는 axios 에서 **API를 호출하여 결과를 받아올때까지 대기하는 비동기 함수**이다.

---
  
# 연결문서
