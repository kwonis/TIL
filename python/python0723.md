# 비시퀀스 데이터 구조

## 딕셔너리
키가 중복되지 않고 순서가 없는 컬렉션

|메서드|설명|
|---|---|
|D.clear()|모든 키/값 제거ㅣ|
|D.get(k)|키에 연결된 값 반환 키가 없으면 None|
|D.get(k,v)|키에 값 없으면 v|
|D.keys()|키를 모은 객체 반환|
|D.values()|값을 모은 객체 반환|
|D.items()|키/값 쌍을 모은 객체|
|D.pop(k)|키 k를 제거하고 연결됐던 값 반환 없으면  오류|
|D.pop(k,v)|없으면 v 반환|
|D.setdefault(k)|키 k 와 연결 값 반환|
|D.setdefault(k,v)|k가 키가 아니면 v와 연결한 키 k를 추가하고 v를 반환|
|D.update(other)|키가 있으면 other 값으로 대체 또는 키/값을 추가  (key = value 와 같은 인자 값으로도 추가 가능)|

```python
for i,j in person.items():
  print(i)
  print(j)
  # name,Alice,age,25
```

```python
person = {'name': 'Alice', 'age': 25}
print(person.pop('age')) # 25
print(person) # {'name':Alice}
```

```python
person = {'name': 'Alice', 'age': 25}
print(person.setdefault('country','KOREA')) # KOREA
print(person) # {'name': 'Alice', 'age': 25, 'country': 'KOREA'}

print(person.setdefault('country'))
print(person) # {'name': 'Alice', 'age': 25, 'country': None}
``` 

## set
중복이 안되고 순서없다. {}로 사용된다.
빈 set 는 a=set()

|메서드|설명|
|---|---|
|s.add()|세트에 x를 추가 있다면 변화 없음|
|s.clear()|세트 모든 항목 제거|
|s.remover()|x를 제거 없을경우 에러|
|s.pop()|임의 항목 반환하고 해당항목을 제거|
|s.discard(x)|항목 x를 제거 에러가 없음|
|s.update(iterable)|expend 와같이 연속성 요소 추가|

## 세트의 집합 메서드
|메서드|설명|연산자|
|---|---|---|
|set1.difference(set2)|차집합|set1 -set2
|set1.intersection(set2)|교집합|set1 &set2
|set1.issubset(set2)|set1가 set2에 포함|set1 <=set2
|set1.issuperset(set2)|set1이 set2를 가지고 있으며|set1 >=set2
|set1.union(set2)|합집합|set1 :set2


### 해시 테이블
해시 함수를 사용하여 변환한 값을 색인을 삼아 키와 데이터를 저장하는 자료구조
-> 데이터를 효율적으로 저장하고 검색하기 위해 사용

해시 함수를 통해 해시 값으로 만들어  인덱스로 사용하기 위해 저장 또는 검색

파이썬 재실행시 테이블 재배치

set()에 pop시 해시 테이블에 인덱스로 작동

해시 (Hash) 임의의 수
- 임의의 크기를 가진 데이터를 고정된 크기의 고유한 값으로 변환하는 것

해시 함수
- 임의의 길이의 데이터를 받아 고정된 길이의 데이터로 출력하는 함수
- 파이썬 실행마다 변경 되기에 해시값이 바뀌는데 큰 영향

## 파이썬에서의 해시 함수
객체의 타입에 따라 달라집
정수는 정숫값으로 사용 - 효율적으로 사용하기 위해 일을 덜 하기 위해


### set의 pop 메서드의 결과와 해시 테이블의 관계
- 무작위 가 아니라 임의라는 의미에서 무작위
-> 해시 테이블에 나타나는 순서대로 반환하는 것

해시 함수에 인풋을 넣으면 정수로 아웃풋이 온다.

가변데이터가 있으면 그것은 해시함수가 되지않는다.

### 파이썬 표기법

BNF
프로그래밍 언어의 문법을 표현하기 위한 표기법

EBNF
확장한 표기ㅣ법

|메서드|설명|
|---|---|
|[]|선택적 요소|
|{}|0번 이상 반복|
|()|그룹화|

사용이유 문서상으로는 통일해서 보기쉽게 하기 위해서이다.