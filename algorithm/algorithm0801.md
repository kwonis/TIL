# 검색
배열에 저장되어있는 자료 중 원하는 항목을 찾는 작업

종류
- 순차 검색
- 이진 검색
- 해쉬

### 순차  검색
일렬로 되어 있는 자료를 순서대로 검색하는 방법

수가 많고 검색에 수가 많아 지면 시간이 늘어나 비효율적

사용 시 평균 비교 회수 (n+1)/2
시간 복잡도 : O(n)

```python
def sequentuial_search(a,n,key)
    i = 0
    while i<n and a[i] !=key:
      i +=1
    if i <n : return i
    else : return -1

for i in range(n):
  if a[i] == key:
    return i
return -1  
```

검색과정 
키 값과 원소의 키 값을 비교해서 크면 검색 종료
끝까지 가는게 아니라 찾을 키값보다 작아지면 뒤에 없으니 종료

```python
def sequentuial_search(a,n,key)
    i = 0
    while i<n and a[i] < key:
      i +=1
    if i <n and a[i] ==key: return i
    else :
      return -1
### i<n and a[i] 인덱스 검사가 최우선 기억하기.    

for i in range(n-1):
  if a[i] == key:
    return i
  elif a[i]>key:
    return -1
return -1  
```
### 이진 검색
정렬되어 있을때 가운데 원소를 찾고 찾는 값과 비교해서 적으면 왼쪽으로 크면 오른쪽으로

그걸 여러번 반복해서 찾기

### 고유번호를 가져와서
하나의 항목으로 검색하고 나머지내용을 찾는다.

데이터베이스 인덱스는 이진 탐색 트리 구조로 되어있다.

### 선택 정렬
코드는 단순하지만
시간 복잡도 O(n**2) 높다

```python 
def sekectionSort(a,N):
  for i in range(N-1): # 구간의 시작
    min_idx=i # 기준위치를 최솟값 위치로 가정
    for j in range(i+1,N):#
      if a[min_idx]> a[j]:
        min_idx = j
    a[i],a[min_idx] = a[min_idx],a[i]
```

### 셀렉션 알고리즘
k번째로 작은 원소를 찾는 알고리즘

```python
def selct(arrk):
  for i in range(0,k):
    min_index =i
    for j in range(i+1,len(arr)):
      if arr[min_index] > arr[j]:min_index=j
    arr[i],arr[min_index] = arr[min_index], arr[i]
  return arr[k-1]
```