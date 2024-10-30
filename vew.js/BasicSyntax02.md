# computed()
계산된 속성을 정의하는 함수

- 미리 계산된 속성을 사용하여 템플릿에서 표현식을 단순하게 하고 불필요한 반복 연산을 줄임

### 특징
- 반환되는 값은 computed ref이며 일반 refs와 유사하게 계산된 결과를.value로 참조 할 수 있음(템플릿에서는.value 생략 가능)
- computed 속성은 의존된 반응형 데이터를 자동으로 추적
- 의존하는 데이터가 변경될 떄만 재평가
  - restOfTodos의 계산은 todos에 의존하고 있음
  - 따라서 todos가 변경될 때만 restOfTodos가 업데이트 됨
```js
const restOfTodos = computed(() => {
  return todos.value.length >0 ? '아직 남았다' : '퇴근!'
})
```

computed와 동일한 로직을 처리할 수 있는 method
- computed 속성 대신 method로도 동일한 기능을 정의할 수 있음

```js
const getRestOfTodos = function() {
  return todos.value.length > 0 ? '아직 남았다' : '퇴근!'
}
<p>{{getRestOfTodos()}}</p>
```
computed와 method 차이
- compute 속성은 의존된 반응형 데이터를 기반으로 캐시됨
- 의존하는 데이터가 변경된 경우에만 재평가됨
- 즉, 의존된 반응형 데이터가 변경되지 않는 한 이미 계산되 결과에 대한 여러 참조는 다시 평가할 필요 없이 이전에 계산된 결과를 즉시 반환
- 반면 method 호출은 다시 렌더링 발생할 때마다 항상 함수를 실행

### Cache(캐시)
- 데이터나 결과를 일시적으로 저장해두는 임시 저장소
- 이후에 같은 데이터나 결과를 다시 계산하지 않고 빠르게 접근할 수 있도록 함

computed - 의존된 데이터가 변경되면 자동으로 업데이트
method - 호출해야만 실행됨

