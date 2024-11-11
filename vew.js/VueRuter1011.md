# Routing
네트워크에서 경로르 선택하느 프로세스
- > 웹 애플리케이션에서 다른 페이지 간의 전환과 경로를 관리하는 기술

ssr - 서버에서 렌더
csr - 클라이언트에서 렌더

router를 yes로 하여 시작

App.vue 파일에
``js

import { RouterLink, RouterView } from 'vue-router'

<RouterLink to ='/'> Home</RouterLink>

<RouterView />
```

router폴더내에 index.js 파일에 url 작성 필요.

views 일반 컴포넌트와 구분하기 위해 컴포넌트 이름을 View로 끝나도록 작성하는 것을 권장


라우팅 기본
1. index.js에 라우터 관련 설정 작성(주소,이름,컴포넌트)
2. RouterLink의 'to' 속성으로 index.js에서 정의한 주소 값(path)을 사용
3. RouterLink클릭 시 경로와 일치하는 컴포넌트가 RouterView에서 렌더링 됨

  
## Named Routes 예시
```
<RouterLink :to="{name:home}"> 
```

- 하드 코딩된 URL을 사용하지 않아도 됨
- URL 입력 시 오타 방지

## 동적 경로 매칭
url에 일부를 변수로 설정


# 프로그래밍 방식 네비게이션
- 프로그래밍으로 URL 이동하기
- router의 인스턴스 메서드를 사용해 RouterLink <a> 태그를 만드는 것처럼 프로그래밍으로 네비게이션 관련 작업을 수행할 수 잇음

router.push() 뒤로가기 가능  router.replace() 뒤로가기 불가능

# Navigation Guard
Vue router를 통해 특정 URL에 접근할 때 다른 URL로 redirect를 하거나 취소하여 내비게이션을 보호

1. 전역가드
   - 애플리케이션 전역에서 모든 라우트 전환에 적용되는 가드
2. 라우터 가드
   - 특정 라우트에만 적용되는 가드
3. 컴포넌트 가드
  - 컴포넌트 내에서만 적용되는 가드

router.beforeEach()
다른 URL로 이동하기 직전에 실행되는 함수

```js
router.beforeEach((to,from)=>{
  return false 또는 retrun {name:'About'}
})
```


router.beforeEnter()
특정 route에 진입했을 때만 실행되는 함수

onBeforeRouteLeave()
- 현재 라우트에서 다른 라우트로 이동하기 전에 실행

onBeforeRouteUpdate()
- 이미 렌더링 된 컴포넌트가 같은 라우트 내에서 업데이트 되기 전에 실행
