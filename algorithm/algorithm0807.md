# Meomoization
메모이제이션
이전에 실행한 값을 메모리에 저장하여 다시 계산하지 않도록해 실행속도를 빠르게 하는 기술

```python
#memo를 위한 배열을 할당하고 ,모두 0으로 초기화한다
#memo[0]을 0으로 memo[1]는 1로 초기화 한다.

def fibo1(n):
  global memo
  if n>=2 and memo[n]==0:
    memo[n] =fibo1(n-1) +fibo1(n-2)

memo =[0] * (n+1)
memo[0] =0
memo[1] =1

```

# DP
동적 계획 알고리즘은 그리디 알고리즘과 같이 최적화 문제를 해결하는 알고리즘

작은부분부터 해결 하여 크기가 큰 부분 해결하는 방법

```python
def fibo2(n):
  f =[0]*(n+1)
  f[0]=0
  f[1]=1
  for i in ragne(2,n+1):
    f[i] =f[i-1]+i[i-2]

return f[n]

```
DP의 구현 방식
- recursive
- iterative

# DFS(깊이우선탐색)

비선형구조인 그래프 구조는 모든 자료를 빠짐없이 검색하는 것이 중요

지나간는 과정을 저장하고 막혔을때 다시 이전 저장한곳으로 돌아가는 작업을 반복하여 모든 자료를 검색하는 것

이외에도 너비 우선 탐색(BFS)도 존재


```python
visited=[]
stack =[]
DFS(v)
```
![DFS 알고리즘](/algorithm/dfsalgo.PNG)


