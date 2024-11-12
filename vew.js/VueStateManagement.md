## State Management

상태 관리
Vue 컴포넌트는 이미 반응형 상태를 관리하고 있음
-> 상태 === 데이터

# State management libray (Pinia)

npm create vue@latest
하고 pinia를 yes로

```js
import { ref, computed } from 'vue'
import { defineStore } from 'pinia'

export const useCounterStore = defineStore('counter', () => {
  const count = ref(0)  //state
  const doubleCount = computed(() => count.value * 2) //getters
  function increment() {
    count.value++
  } // actions

  return { count, doubleCount, increment } //반환은 필수 
})


```

1. Pinia 구성 요소 - 'store'
- 중앙 저장소
- 모든 컴포넌트가 공유하는 상태, 기능 등이 작성됨
- defineStore()의 반환 값의 이름은 use와 store를 사용하는 것을 권장
- defineStore()의 첫번째 인자는 애플리케이션 전체에 걸쳐 사용하는 store의 고유 ID

2. 'state'
   - 반응형 상태
   - ref() === state'

3. 'getters'
   - 계산된 값
   - computed() === getters

4. 'actions'
   - 메서드
   - function() === actions

Setup Stores의 반환 값
- pinia의 상태들ㅇ르 사용 하려면 반드시 반환해야함
- store에서는 공유 하지 않는 private한 상태 속성을 가지지 않음.

5. 'plugin'
   - 애플리케이션의 상태 관리에 필요한 추가 기능을 제공하거나 확장하는 도구나 모듈
   - 애플리케이션의 상태 관리를 더욱 간편하고 유연하게 만들어주며 패키지 매니저로 설치 이후 별도 설정을 통해 추가 됨

## State
- 각 컴포넌트 깊이에 관계없이  store 인스턴스로 state에 접근하여 직접 읽고 쓸수 있음
- 만약 store에 state를 정의하지 않았다면 컴포넌트에서 새로 추가할 수 없음

# Local Storage
-페이지를 새로 고침하고 브라우저를 다시 실행해도 데이터가 유지
쿠키와 다르게 네트워크 요청시 서버로 전송되지 않음
여러 탭이나 창 간에 데이터를 공유 할 수 있음

## pinia-pligin-persistedstate
- 웹 애플리케이션의 상태를 브라우저의 local storage나 session storage에 영구적으로 저장하고 복원하는 기능을 제공

npm i pinia-plugin-persistedstate

```js

//main.js
import piniaPluginPersistedstate from 'pinia-plugin-persistedstate'

import { createApp } from 'vue'
import { createPinia } from 'pinia'
import App from './App.vue'

const app = createApp(App)
const pinia =createPinia()
pinia.use(piniaPluginPersistedstate)
app.use(pinia)

app.mount('#app')

//count.js
 return { todos,addTodo,deleteTodo,updateTodo,doneTodosCount}
},{persist:true}//추가

```