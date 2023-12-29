---
title : "Vue CDN"
excerpt : "Vue CDN"
toc : true
toc_sticky : true
toc_label : "Vue CDN"
categories:
- VueStudy
tags:
- [Vue, Study, FrontEnd]
last_modified_at: 2023-10-30T08:00:00-10:00:00
---

# 날짜 : 2023-10-30 12:25

# 태그 : #Vue #Study #FrontEnd 
---

# 내용

## [CDN](../../webcommon/webcommon-CDN)을 이용한 vue 

### CDN link

```javascript
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
```

### CDN을 사용한 기본 포맷

```javascript
<!DOCTYPE html>  
<html lang="en">  
  
<head>  
    <meta charset="UTF-8">  
    <meta name="viewport" content="width=device-width, initial-scale=1.0">  
    <title>Document</title>  
</head>  
  
<body>  
<div id="app">  
    //UI 정의
</div>  
  
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>  
<script>  
    const {createApp, ref} = Vue  
    const app = createApp({  
        setup() {  
		    // 변수 및 함수
            return {  
            //변경된 값을 UI에 반영하고 싶은 변수 및 함수
            }  
        }  
    })  
    app.mount("#app")  
</script>  
</body>  
  
</html>
```

### Sample

```javascript
<body>
    <div id="app">
        <h1>{{message}}</h1>
        <button @click="count++">
            Count is : {{count}}
        </button>
    </div>
    <script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
    <script>
        const { createApp, ref } = Vue
        const app = createApp({ 
            setup() {
                const message = ref("Hello Vue!!");
                const count = ref(0);
                return {
                    message,
                    count,
                }
            }
        })
        app.mount('#app')
    </script>
</body>
```

-  Vue 객체에서 구조분해 할당 가져오기

```javascript
	const { createApp, ref } = Vue 
```

- Vue 인스턴스 생성

```javascript
	const app = createApp({ 
	...
	)}
```

- 반응성을 가진 참조 변수 선언

```javascript
	const message = ref("Hello Vue!!");
```

- \#app 라는 DOM 내부에서 Vue 반응성 기능을 사용할 수 있도록 Vue 인스턴스를 연결

```javascript
	app.mount('#app')
```

- 진입점

```javascript
	setup() {
	...
	}
```

### LiveServer 결과
  
![image](../../assets/images/VueCDNSample.png)

### binding

#### Object를 binding 하는 방법

```javascript
	<div :class="{active : isActive}">Text</div>
	
    <script>
        const { createApp, ref } = Vue

        const app = createApp({

            setup() {
                const isActive = ref(false);
                const activeClass = ref('active')
                const infoClass = ref('text-primary')
                return {
                    isActive,
                    activeClass,
                    infoClass,
                }
            }
        })
        app.mount("#app")
    </script>
```

##### Array를 binding 하는 방법

```javascript
	<div :class="[activeClass, infoClass]">Text</div>
    
    <script>
        const { createApp, ref } = Vue

        const app = createApp({

            setup() {
                const isActive = ref(false);
                const activeClass = ref('active')
                const infoClass = ref('text-primary')
                return {
                    isActive,
                    activeClass,
                    infoClass,
                }
            }
        })
        app.mount("#app")
    </script>
```

### Handler

#### Inline

```javascript
	<button @click="greetings('Hello')">바꾸자</button>
	<script>
		const { createApp, ref } = Vue
		const app = createApp({
			setup() {
				const count = ref(0)
				const message = ref("")
				const increaseNum = function (event){
					console.log(count) // ref 객체
					console.log(count.value) // value
					count.value++
				}
				const greetings = function(msg){
					message.value = msg
				}
				return {
					count,
					increaseNum,
					message,
					greetings,
				}
			}
		})
		app.mount("#app")
	</script>
```

#### Method

```javascript
	<div id="app">
		{{count}}
		<button @click="increaseNum">+</button>
	</div>
	<script>
		const { createApp, ref } = Vue
		const app = createApp({
			setup() {
				const count = ref(0)
				const increaseNum = function (event){
					console.log(count) // ref 객체
					console.log(count.value) // value
					count.value++
				}
				return {
					count,
					increaseNum,
				}
			}
		})
		app.mount("#app")
	</script>
```

---

# 연결문서