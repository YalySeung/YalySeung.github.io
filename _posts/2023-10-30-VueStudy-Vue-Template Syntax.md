---
title : "Vue-Template Syntax"
excerpt : "Vue-Template Syntax"
toc : true
toc_sticky : true
toc_label : "Vue-Template Syntax"
categories:
- VueStudy
tags:
- [Vue, FrontEnd, Study]
last_modified_at: 2023-10-30T08:00:00-10:00:00
---

# 날짜 : 2023-10-30 12:28

# 태그 : #Vue #FrontEnd #Study 
---

# 내용

## Template Syntax

### Text Interpolation

```javascript
<p>{{message}}</p>
```

- ref값을 동적 텍스트로 렌더링 하는 방법
- 이중괄호 문법 또는 콧수염 구문이라고도 한다.
- 식별자나 경로 이외에 Javascript 표현식도 사용 가능하다.
- 주로 텍스트 삽입시에만 사용한다.

```javascript
<h1>{{ message.split('').reverse().join('') }}</h1>
```

### HTML 출력
- [Text Interpolation](#text-interpolation) 은  데이터를 html 이 아닌 일반 텍스트로 해석
- 실제 html 출력을 위해서는 [v-html](../../VueStudy/VueStudy-Vue-Directive#v-html) Directive를 사용해야 한다.

```javascript
<p>v-html 디렉티브 사용: <span v-html="rawHtml"></span></p>
```

### Binding

#### Boolean 속성 Binding
- 속성의 표시 여부를 Boolean 속성의 변수로 분기

```javascript
<button :disabled="isButtonDisabled">버튼</button>
```

#### Object Binding
- ex1)

```javascript
const classObject = reactive({ active: true, 'text-danger': false })

<div :class="classObject"></div>
```

- ex2)

```javascript
const isActive = ref(true)  
const error = ref(null)  
  
const classObject = computed(() => ({  
  active: isActive.value && !error.value,  
  'text-danger': error.value && error.value.type === 'fatal'  
}))

<div :class="classObject"></div>
```

#### Array Binding

```javascript
const activeClass = ref('active')
const errorClass = ref('text-danger')

<div :class="[activeClass, errorClass]"></div>
```

### javascript 표현식 사용
- vue는 모든 데이터 바인딩 내에 javascript 표현식 지원
	- 이중괄호 내부
	- 모든 [Vue-Directive](../../VueStudy/VueStudy-Vue-Directive) 속성 내부
- 하나의 단일 표현식만 가능
- 함수호출 가능

```javascript
{{ number + 1 }}  
{{ ok ? '예' : '아니오' }}  
{{ message.split('').reverse().join('') }}  
<div :id="`list-${id}`"></div>
{{ formatDate(date) }}
```

---

# 연결문서
- [Vue-Directive](../../VueStudy/VueStudy-Vue-Directive)