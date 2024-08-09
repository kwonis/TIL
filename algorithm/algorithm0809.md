# 부분집합
부분집합에 개수는 2**n개이다.

powerset을 구하는 백트래킹 알고리즘

```python
def backtrack(a,k,n):# 주어진배열, 결정할 원소,원소개수
    c = [0]* maxcandidates

    if k == n:
      process_solution(a,k)
    else:
      ncandidates = construct_candidates(a,k,n,c)
      for i in range(ncandidates):
          a[k] =c[i]
          backtrack(a,k+1,n)

def construct_candidates(a,k,n,c):
  c[0]=True
  c[1]=False
  return 2

def process_solution(a,k):
  for i in range(k):
    if a[i]:
      print(num[i],end ='')
    print()

maxcandidates =2
nmax =4
a =[0] * nmax
num =[1,2,3,4]
backtrack (a,0,nmax)
```

# 순열

집합 {1,2,3}에서 모든 순열을 생성하는 함수

```python
for i1 in range(1,4):
  for i2 in range(1,4):
    if i2 != i1:
      for i3 in range(1,4):
        if i3!=i1 and i3!=i2:
          print(i1,i2,i3)
```

```python
def backtrack(a, k, n):
  c = [0] * maxcandidates

  if k==n :
    for i in range(0,k):
      print(a[i], end='')
    print(0)
  else:
    ncandidates =construct_candidates(a,k,n,c)
    for i in range(ncandidates):
      a[k] = c[i]
      backtrack(a,k+1,n)

def construct_candidates(a,k,n,c):
  in_perm =[False] * (nmax +1)

  for i in range(k):
    in_perm[a[i]] =True
  ncandidates =0
  for i in range(1,nmax+1):
    if in_perm[i] ==False:
      c[ncandidates] =i
      ncandidates +=1
  return ncandidates
```

# 가지치기
