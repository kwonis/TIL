# Vue 사용예시
```js

  <div id="app">
    <h1>{{message}}</h1>
    <button v-on:click="count++">{{count}}</button>
  </div>
  <script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
    const { createApp, ref}  = Vue

    const app = createApp({
      setup(){
        const message = ref('Hello vue!')
        const count =ref(0)

        return {
          message,
          count
        }
      }
    })

    app.mount('#app') //합치기 마운팅 
```

vue의 2가지 핵심기능

1. 선언적 렌더링
   -  표준 HTML을 확장하는 Vue 템플릿 구문을 사용하여 JavaSript 상태를 기반으로 화면에 출력될 HTML을 선언
2. 반응성
   - JavaScript 상태 변경을 추적하고, 변경사항이 발생하면 자동으로 DOM을 업데이트

# ref()
반응형 상태를 선언하는 함수
- .value 속성이 있는 ref 객체로 래핑하여 반환하는 함수 
- ref로 선언된 변수의 값이 변경되면,해당 값을 사용하는 템플릿에서 자동으로 업데이트\
- 인자는 어떠한 타입도 가능


