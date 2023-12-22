---
title : "VueScript Syntax"
excerpt : "VueScript Syntax"
toc : true
toc_sticky : true
toc_label : "VueScript Syntax"
categories:
- VueStudy
tags:
- [Vue, Study, FrontEnd]
last_modified_at: 2023-10-26T08:00:00-10:00:00
---

# 날짜 : 2023-10-26 14:13

# 태그 : #Vue #Study #FrontEnd
---

# 내용

## Script Syntax

### ref
- 반응형 변수 사용 키워드

```javascript
<script>  
import { ref } from 'vue'  
  
const message = ref('안녕 Vue!')  
message.value = '변경된 텍스트'
</script>
```

- 반응형 변수.value : 내부 값을 노출하는 객체 생성

#### ref sudo code

```javascript
const myRef = {  
  _value: 0,  
  get value() {  
    track()  
    return this._value  
  },  
  set value(newValue) {  
    this._value = newValue  
    trigger()  
  }  
}
```

- getter에서 value를 return 하기 전 tracking 수행
- setter에서 value를 할당한 후 trigger를 수행

### reactive
- 객체 자체를 반응형으로 변경
- reactive 반환값을 원본 객체와 같지 않고 객체를 재정의한 Proxy
- 원본 객체를 변경해도 업데이트가 트리거되지 않음
- 객체, 배열 및 컬렉션 유형에만 작동
- 전체 객체를 대체할 수 없다.
- 분해 할당에 친화적이지 않음

```javascript
import { reactive } from 'vue'  
  
const state = reactive({ count: 0 })
```

### nextTick
- DOM이 업데이트 되는 다음 tick 까지 대기

```javascript
import { nextTick } from 'vue'  
  
async function increment() {  
count.value++  
await nextTick()
```

### computed
- 의존된 반응형 데이터를 기반으로 캐시된다.
- 반응형 데이터를 포함한 복잡한 논리의 경우 사용
- 불필요한 반복연산을 줄임
- 반환값을 computed ref
- computed에서 사용된 변수가 변경되면 콜백함수 호출
- return 키워드가 필수

#### import

```javascript
const {computed} = Vue
```

#### Example

```javascript
<script setup>  
import { reactive, computed } from 'vue'  
  
const author = reactive({  
  name: 'John Doe',  
  books: [  
    'Vue 2 - Advanced Guide',  
    'Vue 3 - Basic Guide',  
    'Vue 4 - The Mystery'  
  ]  
})  
  
//계산된 ref
const publishedBooksMessage = computed(() => {  
  return author.books.length > 0 ? 'Yes' : 'No'  
})  
</script>  
  
<template>  
  <p>책을 가지고 있다:</p>  
  <span>{{ publishedBooksMessage }}</span>  
</template>
```

### watch
- 반응형 데이터를 감시
- 감시하는 데이터가 변경되는 콜백함수 호출

#### import

```javascript
import { watch} from 'vue'
```

#### Example

```javascript
const count = ref(0)  
const countWatch = watch(count, (newValue, oldValue) => {  
  console.log(`newValue : ${newValue} oldValue : ${oldValue}`)  
})

<button @click="count++">+</button>  
<p>Count : {{ count }}</p>
```

### watcheffect
- Vue3부터 사용 가능
- watch + 여러개의 의존성을 가질 수 있다.

#### import

```javascript
import {watchEffect} from 'vue'
```

## 활용 예시

### computed, watch

```javascript
import {ref, computed, watch} from 'vue'  
  
const bookInfo = computed({  
      get: () => `${title.value} - ${author.value}`,  
      set: (newValue) => {  
        const parts = newValue.split('-')  
        title.value = parts[0]  
        author.value = parts[1]  
      }  
    }  
)  
  
const title = ref('기초')  
const author = ref('김')  
const bookInfoModel = ref(bookInfo.value)  
  
watch(bookInfoModel, (newValue) => {  
  const parts = newValue.split('-')  
  title.value = parts[0].trim()  
  author.value = parts.length > 1 ? parts[0].trim() : ''  
  author.value = parts.length > 1 ? parts[1].trim() : ''  
})

<div>  
  <p>제목 : {{ title }}</p>  
  <p>저자 : {{ author }}</p>  
  <p>전체 정보 : {{ bookInfo }}</p>  
  <input v-model="bookInfoModel">  
</div>
```

---

# 연결문서
- [html-tags](../../webcommon/webcommon-htmltags)
- [Vue-Directive](../../vuestudy/vuestudy-VueDirective)