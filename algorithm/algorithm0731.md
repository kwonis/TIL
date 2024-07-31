# 2차원 배열

2차원 배열을 만들어 둘때에는 
```python
arr2=[[0] * 3 for _ in range(2)] 
 # [[0, 0, 0], [0, 0, 0]]

for i in range(2):
    print(*arr[i])
    # 0 0 0
    # 0 0 0

for i in range(2):
    for j in range(3):
        print(arr[i][j],end = ' ')
    print() 
    # 0 0 0
    # 0 0 0  

arr1=[[0]*3]*2 # [[0, 0, 0], [0, 0, 0]] 
하지만 하면 안된다 이유는 하나의 값을 변경하면 해당 말고도 추가로 변경 되기에 
```

# 배열 순회

### 행 우선 순회
```python
for i in range(n):
  for j in range(m):
    f(arr[i][j])
#행의 합중 최댓값은?
max_v=0 #값에 따라
for i in range(n):
  sum =0
  for j in range(m):
    sum +=arr[i][j]
    if max_v < sum:
      max_v = sum
```

### 열 우선 순회
```python
for i in range(n):
  for j in range(m):
    f(arr[j][i])
```

### 지그재그 순회
```python
for i in range(n):
  for j in range(m):
    f(arr[i][j + (m-1-2*j)*(i%2)#i가 짝수일때에는 정방향])
```

### 델타를 이용한 2차 배열 탐색
```python
# 현재 존재하는 위치 (i,j)
# 오른쪽으로 이동 (i+0,j+1)
# 아래 이동 (i+1,j+0)
# 왼쪽 이동 (i+0,j-1)
# 위로 이동 (i-1,j+0)
di[] <- [0,1,0,-1]
dj[] <- [1,0,-1,0]

for k :0 -> 3
ni - i + di[k]
nj - j + dj[k]
```
```python
for k in range(4):
  ni = i +di[k]
  nj = j +dj[k]
  if 0<= ni <N and 0<= nj <N

```
### 전치 행렬
대각선을 기준으로 뒤집어진 행렬
```python
for i in range(3):
  for j in range(3):
    if i <j: # 두번 변하는 상황을 고려하기 위해서
      arr[i][j],arr[j][i] =arr[j][i],arr[i][j]
```
원소 접근
i < j 오른쪽 
i == j 대각선
i > j 왼쪽아래
2-i == j 반대 대각선


### 부분집합 합
부분집합 갯수 집합의 원소가 n개 일 때, 공집합을 포함한 부분집합의 수는 2**n 
```python 
bit =[0,0,0,0]
for i in range(2):
  bit[0] =i
  for j in range(2):
    bit[1] =j
    for k in range(2):
      bit[2] =k
      for l in range(2):
        bit[3] = l

```
### 비트 연산자
& and
| or
<<왼쪽으로 이동
>> 오른쪽으로 이동

ㅑ& (1<<j): i의 j 번째 비트가 1인지 아닌지를 검사

```python
arr =[3,6,7,1,5,4]
n =len(arr)
for i in range(1<<n):
  for j in range(n)
    if i &(1<<j):
      print(arr[j],end=",")
    print()
  print()
```

```python
N = int(input())
arr =[list(map(int,input().split())) for _ in range(N)]

di =[0,1,0,-1]
dj =[1,0,-1,0]

total =0
for i in range(N):
    s = 0
    for j in range(N): # NxN 배열의 모든 원소에 대해
        # i,j 원소의 4방향 원소에 대해
        for k in range(4):
            ni = i+ di[k]
            nj = j +dj[k]
            if 0<=ni < N and 0<=nj <N:
                s += abs(arr[i][j] - arr[ni][nj])                        #실존 하는 인접원소 ni,nj
        total += s
print(total)
```
# 비트 연산자
# 부분집합 - bit 연산자 를 활용
# N개의 원소
arr = [1,2,6,4,7]
N = len(arr) # 5

# print(1<<0) # 1
# print(1<<1) #2
# print(1<<2) #4
# print(1<<3) #8
# print(1<<4) #16
# print(1<<5) #32

print((1<<0) & (1<<0)) #000001 의 #000001 번째 비트가 1인지 : True > arr[0]
print((1<<0) & (1<<1)) #000001 의 #000010 번째 비트가 1인지 : False
print((1<<0) & (1<<2)) #000001 의 #000100 번째 비트가 1인지 : False
#                       ...
#                       ...
#                  결국 #000001 에서 1 에 해당하는 값만 한 줄 나열 = 부분집합 1개 완성!
#                  결국 #000010 에서 1 에 해당하는 값만 한 줄 나열 = 부분집합 1개 완성!
#                  ...

for i in range(1 << N) :
    for j in range(N) :
        if i & (1 << j) : # i의 j번째 비트가 1인지
            print(arr[j],end=",")
    print()
print()
