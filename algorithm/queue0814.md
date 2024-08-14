# BFS
너비우선탐색은 인접한 정점을 먼저 모두 방문한 후에 방문했던 정점을 시작점으로 다시 인접한 정점들을 차례로 방문

```python
'''
7 8
4 2 1 2 1 3 5 2 4 6 5 6 6 7 3 7
'''

def bfs(s,V):
    visited =[0] * (V+1)
    q=[]
    q.append(s)
    visited[s]=1
    while q:
        t =q.pop(0)
        print(t)
        for w in adjl[t]:
            if visited[w] ==0:
                q.append(w)
                visited[w] = visited[t]+1
V,E = map(int,input().split()) #V는 마지막 정점 번호/E는 간선 갯수
adjl =[[] for _ in range(V+1)]
arr=list(map(int,input().split()))

for i in range(E):
   v1,v2 = arr[i*2],arr[i*2+1]
   adjl[v1].append(v2)
   adjl[v2].append((v1))

bfs(1,7)
```