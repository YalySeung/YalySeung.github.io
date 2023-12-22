---
title : "Vue-State"
excerpt : "Vue-State"
toc : true
toc_sticky : true
toc_label : "Vue-State"
categories:
- VueStudy
tags:
- [Vue, FrontEnd, Study]
last_modified_at: 2023-11-01T08:00:00-10:00:00
---

# 날짜 : 2023-11-01 14:30

# 태그 : #Vue #FrontEnd #Study
---

# 내용

## Vue 상태관리

### Pinia
- Vue 상태 관리 라이브러리

#### Pinia 프로젝트 생성
  
![image](../../assets/images/CreateVuePiniaProject.png)

#### 프로젝트 구조
  
![image](../../assets/images/VuePiniaProcjectStructure.png)

### Keyword

```javascript
import { ref, computed } from 'vue'  
import { defineStore } from 'pinia'  
  
export const useCounterStore = defineStore('counter', () => {  
  const count = ref(0)  
  const doubleCount = computed(() => count.value * 2)  
  function increment() {  
    count.value++  
  }  
  
  return { count, doubleCount, increment }  
})
```

#### Store
- 중앙 저장소

##### 정의
- stores 디렉토리 경로에 생성

```javascript
import { ref, computed } from 'vue'  
import { defineStore } from 'pinia'  
  
export const useCounterStore = defineStore('counter', () => {  
  const count = ref(0)  
  const doubleCount = computed(() => count.value * 2)  
  function increment() {  
    count.value++  
  }  
  
  return { count, doubleCount, increment }  
})
```

##### 사용

```javascript
import {useCounterStore} from "@/stores/counter";

counter = useCounterStore()

const increaseCount = () => {  
  counter.increment();  
}
```

###### Componenet 전환시 lazy import

```javascript
beforeEnter: (to, from) => {  
    const userStore = import('../stores/user').then(storeModule => {  
        const store = storeModule.useUserStore()  
        const isLogin = store.isLogin  
        if (!isLogin) {  
            alert('로그인 후 이용해주세요')  
            next('/')  
        } else {  
            next()  
        }  
    })  
}
```

#### State
- 반응형 상태

```javascript
const count = ref(0)  
```

#### getters
- 계산된 값

```javascript
const doubleCount = computed(() => count.value * 2)  
```

#### actions
- 메서드
- 함수를 직접 호출 보다는 다른 함수를 만들어 호출하는 방식 권장

```javascript
  function increment() {  
    count.value++  
  }  
```

#### plugin
- 추가 기능을 제공하는 도구나 모듈

---

# 연결문서
- [Vue-프로젝트-Init](../../vuestudy/vuestudy-Vue-프로젝트-Init)