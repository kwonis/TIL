# 이벤트

웹에서의 이벤트
- 화면을 스크롤하는 것
- 버튼을 클릭했을 때 팝업 창이 출력되는것
- 마우스 커서의 위치에 따라 드래그 앤 드롭하는 것
- 사용자의 키보드 입력 값에 따라 새로운 요소를 생성하는것
- ### 웹에서의 모든 동작은 이벤트 발생과 함께한다.

event
무언가 일어났다는 신호,사건  모든 DOM 요소는 이런한 event를 만들어 냄

### event handler
특정 이벤트가 발생했을 떄 실행되는 함수


#### addEventListener()
대표적인 이벤트 핸들러 중 하나
EventTarget.addEventListener(type,handler)

```js
element.addEventListener('click',function(evevt){
  //이벤트 처리
})
```

콜백 함수 특징
- 이벤트 핸들러 내부의 this는 이벤트 리스너에 연결된 요소를 가리킴
- 이벤트가 발생하면 event 객체가 생성되어 첫 번쨰 인자로 전달
  - event 객체가 필요 없는 경우 생략 가능
- 반환 값없음

- 'currentTarget'속성
  - 현재요소
  - 항상 이벤트 핸들러가 연결된 요소만을 참조하는 속성
  - this와같음
- 'target' 속성
  - 이벤트가 발생한 가장 안쪽의 요소를 참조하는 속성
  - 실제 이벤트가 시작된 요소
  - 버블링이 진행 되어도 변하지 않음

```js
<div>
<button></button>
<button></button>
<button></button>
<button></button>
</div>
```
일시 각 버튼만다 주는게 아닌 div에 이벤트 핸들러 주고 
event.target를 이벤트를 다룸


## 이벤트 취소
.preventDefault()
해당 이벤트에 대한 기본 동작을 실행하지 않도록 지정