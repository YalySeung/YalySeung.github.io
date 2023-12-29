---
title : "Vue SFC"
excerpt : "Vue SFC"
toc : true
toc_sticky : true
toc_label : "Vue SFC"
categories:
- VueStudy
tags:
- [Vue, FrontEnd, Study]
last_modified_at: 2023-10-27T08:00:00-10:00:00
---

# 날짜 : 2023-10-27 23:25

# 태그 : #Vue #FrontEnd #Study 
---

# 내용

## SFC
- Single File Component
- 화면, 로직, 스타일을 포함한 하나의 파일(\*.vue)

## Vue의 SFC

```javascript
<script setup>  
</script>  
  
<template>  
</template>  
  
<style scoped>  
</style>
```

####  script
- 논리

#### template
- HTML

#### scope
- css

## 스크립팅 방식

### 옵션 API 방식

```javascript
<script>  
export default {  
  // data()에서 반환된 속성들은 반응적인 상태가 되어 `this`에 노출됩니다.  
  data() {  
    return {  
      count: 0  
    }  
  },  
  
  // methods는 속성 값을 변경하고 업데이트 할 수 있는 함수.  
  // 템플릿 내에서 이벤트 헨들러로 바인딩 될 수 있음.  
  methods: {  
    increment() {  
      this.count++  
    }  
  },  
  
  // 생명주기 훅(Lifecycle hooks)은 컴포넌트 생명주기의 여러 단계에서 호출됩니다.  
  // 이 함수는 컴포넌트가 마운트 된 후 호출됩니다.  
  mounted() {  
    console.log(`숫자 세기의 초기값은 ${this.count} 입니다.`)  
  }  
}  
</script>
```

### 컴포지션 API 방식

```javascript
<script>  
import {ref, onMounted} from 'vue'  
  
// 반응적인 상태의 속성  
const count = ref(0)  
  
// 속성 값을 변경하고 업데이트 할 수 있는 함수.  
function increment() {  
  count.value++  
}  
  
// 생명 주기 훅  
onMounted(() => {  
  console.log(`숫자 세기의 초기값은 ${count.value} 입니다.`)  
})  
</script>
```
``

---

# 연결문서
