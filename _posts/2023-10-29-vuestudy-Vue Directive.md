---
title : "Vue Directive"
excerpt : "Vue Directive"
toc : true
toc_sticky : true
toc_label : "Vue Directive"
categories:
- VueStudy
tags:
- [Vue, Study, FrontEnd]
last_modified_at: 2023-10-29T08:00:00-10:00:00
---
  
---
  
## Directive
- v- 접두사가 있는 특수한 속성
  
```javascript
<p v-if="seen">Hi There</p> 
{: .notice}  
```
  
### 구문
  
```javascript
v-on:submit.prevent="onSubmit"
Name:Argument.Modifier=value
```
  
![image](../../assets/images/DirectiveFormat.png)
  
```javascript
<a v-bind:href="url"> ... </a>   
{: .notice}  
  
<a :href="url"> ... </a> 
{: .notice}  
```
  
```javascript
<a v-on:click="doSomething"> ... </a>   
{: .notice}  

<a @click="doSomething"> ... </a> 
{: .notice}  
```
  
##### 동적 인자
- 디렉티브의 인자를 대괄호로 감싸서 Javascript 표현식 사용 가능
  
```javascript
<a v-bind:[attributeName]="url"> ... </a>   
{: .notice}  

<a :[attributeName]="url"> ... </a> 
{: .notice}  
```  
- 동적인자는 null 또는 문자열로 평가되어야 한다.
- 동적 인자는 공백 및 따옴표를 허용하지 않는다.
- 대문자 이름 허용하지 않는다.
  
### built-in function
  
#### v-bind
  
```javascript
<div v-bind:id="dynamicId"> </div> 
{: .notice}  
<div :id="dynamicId"> </div> 
{: .notice}  
```  
- **단방향 바인딩**
- id 부분은 **인자**
- 콜론 단축문법 
  
##### Boolean 속성에서 v-bind
  
```javascript
<button :disabled="isButtonDisabled">버튼</button> 
{: .notice}  
```  
- true면 해당 속성 표기, false면 해당 속성 제거
  
##### 다중 속성 v-bind
  
```javascript 
const objectOfAttrs = { id: 'container', class: 'wrapper' }

<div v-bind="objectOfAttrs"></div> 
{: .notice}  
```  
- 단일 요소에 여러 속성 바인딩
  
#### v-model
- **양방향 바인딩**
  
```javascript
<div id="app">   
{: .notice}  
    <input type="text" v-model="text1">   
{: .notice}  
    <input type="checkbox" name="" id="" v-model="selected">   
{: .notice}  
    <select name=""  id="1" v-model="selected2">   
{: .notice}  
        <option value="1">1</option>   
{: .notice}  
        <option value="2">2</option>   
{: .notice}  
        <option value="3">3</option>   
{: .notice}  
    </select>   
{: .notice}  
    <input type="checkbox" name="" id="Alice" v-model="selectedName" value="Alice">   
{: .notice}  
    <label for="Alice">Alice</label>   
{: .notice}  
    <input type="checkbox" name="" id="Tom" v-model="selectedName" value="Tom">   
{: .notice}  
    <label for="Tom">tom</label>   
{: .notice}  
</div> 
{: .notice}  

<script>   
{: .notice}  
    const { createApp, ref } = Vue  
    const app = createApp({  
        setup() {  
            const text1 = ref();  
            const selected = ref(false);  
</script> 
{: .notice}  
```
  
##### 수식어
- .lazy : change 이벤트 후 동기화
  
```javascript
<input v-model.lazy="msg" /> 
{: .notice}  
```  
- .number : 사용자 입력자 자동으로 숫자 변환
  
```javascript
<input v-model.number="age" /> 
{: .notice}  
```  
- .trim : 사용자 입력에서 공백 제거
  
```javascript
<input v-model.trim="msg" /> 
{: .notice}  
```
  
#### v-on
  
```javascript
<button v-on:click="increment">{{ count }}</button> 
{: .notice}  
<button @click="increment">{{ count }}</button> 
{: .notice}  
```  
- 이벤트 리스너
- DOM 이벤트를 수신
- @ 단축문법
  
##### 이벤트 객체 획득
  
```javascript
<button @click="warn('아직 양식을 제출할 수 없습니다.', $event)">   
{: .notice}  
  제출하기  
</button>   
{: .notice}  
  
<!-- 인라인 화살표 함수 사용 -->   
{: .notice}  
<button @click="(event) => warn('아직 양식을 제출할 수 없습니다.', event)">   
{: .notice}  
  제출하기  
</button> 
{: .notice}  
```
  
##### 이벤트 수식어
  
|수식어|기능|
|---|---|
|.stop|이벤트 전파 중지|
|.prevent|페이지 리로드 중지|
|.self|엘리먼트 자신일 경우에만 핸들러 실행|
|.capture|내부 엘리먼트에서 클릭 이벤트 핸들러 실행되기 전 현재 엘리먼트에서 먼저 핸들러 실행|
|.once|한번만 실행|
|.passive|이벤트의 기본동작이 발생|
  
##### 입력 키 별칭
- .enter
- .tab
- .delete ("Delete" 및 "Backspace" 키 모두 캡처)
- .esc
- .space
- .up
- .down
- .left
- .right
- `.ctrl`
- `.alt`
- `.shift`
- `.meta`
  
##### 마우스 버튼 수식어
- .left
- .right
- .middle
  
##### .extract
- 이벤트를 트리거하는 데 필요한 시스템 수식어의 정확한 조합 제어
  
```javascript
<!-- Ctrl과 함께 Alt 또는 Shift를 누른 상태에서도 클릭하면 실행됩니다. -->   
{: .notice}  
<button @click.ctrl="onClick">A</button>   
{: .notice}  
  
<!-- 오직 Ctrl만 누른 상태에서 클릭해야 실행됩니다. -->   
{: .notice}  
<button @click.ctrl.exact="onCtrlClick">A</button>   
{: .notice}  
  
<!-- 시스템 입력키를 누르지 않고 클릭해야지만 실행됩니다. -->   
{: .notice}  
<button @click.exact="onClick">A</button> 
{: .notice}  
```
  
##### 마우스 버튼
  
#### v-html
  
```javascript
<div v-html="rawHtml"></div> 
{: .notice}  
```  
- 실제 html 이 출력됨
  
#### v-if
- 요소를 DOM에 조건부로 렌더링
- toggle 비용이 높음
  
```javascript
	<div v-if="name === 'Alice'">Alice</div> 
{: .notice}  
	<div v-else-if="name === 'Cathy'">Cathy</div> 
{: .notice}  
	<div v-else-if="name === 'Tom'">Tom</div> 
{: .notice}  
```
  
##### 주의사항
- v-if는 Directive 이기 때문에 단일 요소에만 연결 가능
- 필요에 따라 template(wrapper) 요소에 여러 요소 연결하여 사용해야 한다.
  
#### v-show
- 표현식 값을 기반으로 요소의 가시성을 전환
- 초기 조건에 관계 없이 항상 렌더링, 초기비용이 더 높다.
  
```javascript
<h1 v-show="ok">안녕!</h1> 
{: .notice}  
```
  
#### v-for
- 반복 요소 사용
- alias 제공
- 반드시 key를 함께 사용
  
```javascript
	<div v-for="(item, index) in myArr">{{index}} / {{item}}</div> 
{: .notice}  
	<div v-for="(value, key, index) in myObj">{{index}} / {{key}} / {{item}}</div> 
{: .notice}  
```
  
```javascript
	<li v-for="(item, index) in items">  
{: .notice}  
		{{ parentMessage }} - {{ index }} - {{ item.message }} 
	</li> 
{: .notice}  
```  
- 속성명의 별칭 추가
  
```javascript
	<li v-for="(value, key) in myObject">  
{: .notice}  
		{{ key }}: {{ value }}
	</li> 
{: .notice}  
```
  
--
  
# 연결문서
- [Vue-Template Syntax](../../vuestudy/vuestudy-Vue-Template-Syntax)