## 카운팅 정렬
항목들의 순서를 결정하기 위해 집합에 각 항목이 몇 개씩 있는지 세는 작업을 하여, 선형 시간에 정렬하는 효율적인 알고리즘
- 제한 사항 
  - 정수나 정수로 표현할 수 있는 자료에 적용

1. 단계 (백만개까지는 가능)
   각 항목들의 발생 횟수를 세고 저장한다.

i,j 와 같은 인덱스는 값을 직접적으로 가져올때는 안쓰는게 좋다.
```python
for x in Data:
  Counts[x] +=1 # counts에서 x에 해당하는 값을 1씩 증가
```
2. 단계
  n까지의 갯수 구하기

```python
for i in range(1,n):
  counts[i] +=counts[i-1]
```
3. 단계
   counts[1]을 감소시키고 Temp에 1을 삽입한다.
   정확한 갯수를 모르기에 가장 마지막에 위치 하고 1을 감소

```python
def Countung_Sort(DATA,TEMP,k):
  COUNTS = [0]*(k+1)

  for i in range(0,len(DATA)):
    COUNTS[DATA[i]] += 1
  
  for i in range (1,k+1):
    COUNTS[i] += COUNTS[i-1]

  for i in range (len(TEMP)-1,-1,-1):
    COUNTS[DATA[i]] -= 1
    TEMP[COUNTS[DATA[i]]] =DATA[i]
```
카운팅 정렬은 크기에 따라 제약이 있다 .

뒤에서 부터 작업을 하는 이유는 앞에서 부터하면 data에 순서와 반대가 되기 떄문이다.

##  Baby-gin Game
0~9 카드중 6장 뽑고 3장의카드가 연속이면 run 동인한 번호는 triplet

6장의 카드가 run과 triplet으로만 구성된 경우 baby-gin

6자리 숫자를 받아 baby- gin 여부를 판단하는 프로그램

- 완전 검색
  모든 경우의 수를 나열하여 확인하는 기법
  경우의 수가 작을 때 유용하다.

## 탐욕 알고리즘
최적해를 구하는 데 사용되는 근시안적인 방법

해 선택 - 실행 가능성 검사 - 해검사 순으로 진행

```python
for i in range(6):
  c[num % 10] +=1
  num //= 10
# 일의 자리부터 하나 씩 카운팅
```
```python
# 무한대의 수  시간이 오래걸려 안 쓰는거 추천 
max_sum = -float('inf')
min_sum = float('inf')
```