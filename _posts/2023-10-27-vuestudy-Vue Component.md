---
title : "Vue Component"
excerpt : "Vue Component"
toc : true
toc_sticky : true
toc_label : "Vue Component"
categories:
- VueStudy
tags:
- [Vue, FrontEnd, Study]
last_modified_at: 2023-10-27T08:00:00-10:00:00
---
  
---
  
## 컴포넌트 간 통신
- vue에서 컴포넌트 간의 데이터 전달은 단방향으로만 가능
- 컴포넌트간의 의존 줄이기, 데이터 일관성 확보를 위함
  
![image](../../assets/images/VueComponentRelation.png)
  
## Props
- 부모 속성이 업데이트 되면 자식에게 전달되지만 반대는 안됨
- 자식 컴포넌트에서 props 변경은 불가
  
### 사용법
  
#### defineProps()
- Child : camelCase 사용
  
```javascript
<script setup>   
{: .notice}  
	import {ref} from "vue"  
	
	defineProps(['myMsg'])  
</script> 
{: .notice}  
```  
- Parent : kebab-case  사용
  
```javascript
<template>   
{: .notice}  
  <Child my-msg="message"/>   
{: .notice}  
</template> 
{: .notice}  
```
  
```javascript
 defineProps({  
  myMsg:String  
})
```
  
## emit 메서드
- $emit(event, ...agrs)
- 콜벡 함수 호출하는 방식으로 동작
  
### 사용법
  
#### 콜벡함수 정의
  
```javascript
<template>   
{: .notice}  
  <Child @some-event="callback"/>   
{: .notice}  
</template>   
{: .notice}  
  
<script setup>   
{: .notice}  
import Child from "./Child.vue"  

const callback = () => {   
{: .notice}  
  alert("이벤트 발생!!")  
}  
</script> 
{: .notice}  
```
  
#### 콜벡 호출
  
```javascript
<template>   
{: .notice}  
  <button @click="$emit('someEvent')">emit</button>   
{: .notice}  
</template> 
{: .notice}  
```
  
#### defindEmits
- 콜백 함수명 선언
  
```javascript
const emit = defineEmits(['updateNameToParent'])
```  
- 콜백 함수 호출
  
```javascript
const onUpdateName = (name) => {   
{: .notice}  
  emit('updateNameToParent', name)  
}
```  
- 콜백함수 연결
  
```javascript
<Child @update-name-to-parent="changeName"/> 
{: .notice}  
```  
---
  
# 연결문서
- [v-on](../../vuestudy/vuestudy-Vue-Script-Syntax#v-on)