---
title : "Vue routing"
excerpt : "Vue routing"
toc : true
toc_sticky : true
toc_label : "Vue routing"
categories:
- VueStudy
tags:
- [Vue, FrontEnd, Study]
last_modified_at: 2023-10-31T08:00:00-10:00:00
---

# 날짜 : 2023-10-31 15:49

# 태그 : #Vue #FrontEnd #Study
---

# 내용

## Vue-Router
- User Input에 따라 동적으로 컴포넌트를 변경

### 환경구성
- vite 프로젝트 생성시, Router 추가
  
![image](../../assets/images/CreateVueWithRouter%201.png)

### 프로젝트 구조
  
![image](../../assets/images/VueRouterProjectStructure.png)

#### views
- [Component](../../vuestudy/vuestudy-Vue-Component)들을 가져와서 사용할 view Directory
- 일반적으로 \* View.vue 파일명 형식 사용

#### App.vue

```javascript
<header>  
  <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />  
  
  <div class="wrapper">  
    <HelloWorld msg="You did it!" />  
  
    <nav>     
     <RouterLink to="/">Home</RouterLink>  
      <RouterLink to="/about">About</RouterLink>  
      <RouterLink :to="{name : 'user'}">User</RouterLink>
    </nav>  </div></header>  
  
<RouterView />
```

#### index.js
- routing 할 View 정보

```javascript
const router = createRouter({  
  history: createWebHistory(import.meta.env.BASE_URL),  
  routes: [  
    {  
      path: '/',  
      name: 'home',  
      component: HomeView  
    },  
    {  
      path: '/about',  
      name: 'about',  
      component: () => import('../views/AboutView.vue')
    },
	{  
	  path:'/user/:id',  
	  name: 'user',  
	  component: () => import('../views/UserView.vue')  
	},  
	{  
	  path:'/:pathMatch(.*)*',  
	  name: 'error',  
	  component: () => import('../views/NotFoundView.vue')  
	}
  ]  
})
```

### 매개변수를 사용한 동적 경로 매칭

#### useRoute
- index.js 에 선언한 createRoute 데이터를 가져옴

##### import

```javascript
import {useRoute} from 'vue-router'
```

### 네비게이션

#### 프로그래밍 방식의 네비게이션

##### router.push

###### import

```javascript
import router from "@/router";
import router from "../router";
---
import {useRouter} from 'vue-router'  
const router = useRouter();
```

###### 사용
- params : 파라미터 전달 필요 시 사용
- query : query 파라미터 전달 필요 시 사용

```javascript
router.push({name: 'home'})
router.push({name: 'user', params: {id: 1}});
router.push({name: 'about', query: {name : 'issac'}});
```

##### router.replace
- 뒤로가기 stack에 쌓지 않고 컴포넌트 전환

##### router.go
- 뒤로가기

```javascript
router.go(-1)
```

- 앞으로 가기

```javascript
router.go(1)
```

#### Navigation Guard
- 특정 url에 접근할 때, 네비게이션 방지

##### 전역 Guard

###### router.beforeEach
- 다른 url로 이동하기 직전에 실행되는 함수
- return 이 없다면 원래 가려던 페이지로 네비게이팅, false 이면 미동작, name을 포함한 객체이면 해당 페이지로 redirecting

```javascript
//index.js
router.beforeEach((to, from) => {  
  console.log('to')  
  console.log(to)  
  console.log('from')  
  console.log(from)  
  return {name : 'home'}
})
```

##### 컴포넌트 Guard

###### router.beforeEnter
- index.js 파일에 Guard 정보 설정

```javascript
{  
  path:'/user/:id',  
  name: 'user',  
  component: () => import('../views/UserView.vue'),  
  beforeEnter: (to, from) => {  
    return {name : 'home'}  
  }  
}
```

##### Router Guard

###### onBeforeRouteLeave
- 현재 라우트에서 다른 라우트로 이동 전에 실행

```javascript
onBeforeRouteLeave((to, from) => {  
  const answer = window.confirm("정말 떠나실건가요?")  
  if (answer === false){  
    return false;  
  }  
})
```

###### onBeforeRouteUpdate
- 이미 렌더링 된 컴포넌트가 같은 라우트 내에서 업데이트 되기 전에 실행

##### notFound 페이지 리다이렉팅
- index.js

```javascript
{  
  path:'/:pathMatch(.*)*',  
  name: 'error',  
  component: () => import('../views/NotFoundView.vue')  
}
```

##### Llazy Loading Routes
- 첫 빌드시 해당 컴포넌트를 로드하지 않고 해당 경로를 처음 방문할 때만 로드

```javascript
 component: () => import('../views/AboutView.vue')
```

---

# 연결문서
- [Vue-프로젝트-Init](../../vuestudy/vuestudy-Vue-프로젝트-Init)
