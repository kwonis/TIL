# Tree
- 비선형 구조
- 계층형 자료구조
- 상위에서 하위로 내려가면서 확장되는 구조

최상위 노드인 루트가 존재하며 나머지는 분리 집합으로 분리될 수 있다.

트리중 트리모양을 따로 때내면 그것을 서브트리로 부른다.

노드 - 트리의 원소
간선 - 노드를 연결하는선. 부모 노드와 자식 노드를 연결
루트 노드 - 트리의 시작 노드
형제 노드 -같은 부모 노드의 자식 노드
조상 노드 - 루트 노드까지 이르는 경로에 모든 노드
서브 트리 - 부모 노드와 연결된 간선을 끊었을 때 생성되는 트리
자손 노드 - 서브 트리에 있는 하위 레벨의 노드들

### 차수 (degree)
노드에 연결된 자식 노드의 수

#### 높이
노드의 높이 : 루트에서 노드에 이르는 간선의 수.
트리의 높이: 트리에 있는 노드의 높이 중에서 가장 큰 값.

형제노드 끼리의 연결은 안된다 / 싸이클이 없다.

# 이진트리
최대 2개의 서브트리를 갖는 특별한 형태의 트리

특성
레벨 i에서의 노드의 최대 개수는 2**i개
높이가 h인 이진 트리가 가질 수 있는 노드의 최소 개수는 (h+1)개 되며, 최대 (2**(h+1)-1) 개가 된다.

### 완전 이진 트리
노드 번호 1번부터 n번까지 빈 자리가 없는 이진 트리

### 편향 이진 트리 
한쪽 방향의 자식 노드만을 가진 이진 트리

## 순회
각 노드를 중복되지 않게 전부 방문 하는 것
비선형이기에 선후 연결 관계를 알 수 없다.

### 순회방법
- 전위순회 :(preorder traversal) :VLR
    부모노드 방문 후, 자식노드를 좌,우 순서로 방문
- 중위순회(inorder traversal):LVR
  - 왼쪽 자식노드, 부모노드, 오른쪽 자식노드 순으로 방문한다.
- 후위순회(postorder traversal):LRV
  - 자식노드를 좌우 순서로 방문한 후, 부모노드로 방문한다.


### 전위 순회
```python
def preorder_traverse(T):
  if T:
    visit(T)
    preorder_traverse(T.left)
    preorder_traverse(T.right)
```

### 중위 순회
```python
def inorder_traverse(T):
  if T:
    inorder_traverse(T.left)
    visit(T)
    inorder_traverse(T.right)
```

### 후위 순회
```python
def postorder_traverse(T):
  if T:
    postorder_traverse(T.left)
    prostorder_traverse(T.right)
    visit(T)
```

 이진트리의 표현 - 배열
 왼쪽은 i*2 오른쪽은 i*2+1
 자식 왼쪽 2*i 오른쪽 2*i+1