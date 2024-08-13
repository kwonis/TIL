# 큐
삽입과 삭제의 위치가 제한적인 자료구조
- 뒤에서는 삽입 하고 앞에서는 삭제
  
## 선입선출구조(LIFO)
front(저장된 원소 중 첫 번째 원소) / Rear(저장된 원소 중 마지막 원소)

큐의 기본 연산 
삽입 : enQueque
삭제 : deQueque

|연산|기능|
|---|---|
|enQueue(item)|큐의 뒤쪽에 원소를 삽입하는 연산|
|deQueue()|큐의 앞쪽에서 원소를 삭제하고 반환하는 연산|
|createQueue()|공백 상태의 큐를 생성하는 연산|
|isEmpty()|큐가 공백상태인지를 확인하는 연산|
|isFull()|큐가 포화상태인지를 확인하는 연산|
|Qpeek()|큐의 앞쪽에서 원소를 삭제 없이 반환하는 연산|

```python
def enQueue(item) :
  global rear
  if isFull() :print('Queue_Full')
  else:
    rear+=1
    Q[rear] = item
```

```python
deQueue():
if(isEmpty()): Queue_Empty()
else:
  front +=1
  return Q[front]
```

공백 상태 - front == rear
포화 상태 - rear ==len(Q) - 1

```python
def Qpeek():
  if isEmpty():print('Queue_Empty')
  else:
    return Q[fornt +1]
```

## 원형 큐
front 변수
공백 상태와 포화 상태 구분을 쉽게 하기 위해 front가 있는 자리는 빈자리로

원형큐
삽입위치 : rear =(rear+1) mod n
삭제위치 : front =(front +1) mod n 

# 우선순위 큐
- 배열을 이용하여 자료 저장
- 원소를 삽입하는 과정에서 우선순위를 비교하여 적절한 위치에 삽입하는 구조 

문제점
-배열을 사용 함으로 시간이나 메모리낭비가 큼

## 버퍼
데이터를 한 곳에서 다른 곳으로 전송하는 동안 그 데이터를 보관하는 메모리의 영역