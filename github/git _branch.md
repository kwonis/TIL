# Git Branch
나뭇가지처럼 여러 갈래로 작업 공간을 나누어 독립적으로 작업할 수 있도록 도와주는 Git의 도구

### 장점
1. 독립된 개발 환경을 형성하기 때문에 원본에 대해 안전
2. 하나의 작업은 하나의 브랜치로 나누어 진행되므로 체계적으로 협업과 개발이 가능
3. 손쉽게 브랜치를 생성하고 브랜치 사이를 이동할수 있음

왜 사용해야 할까??

1. 브랜치를 통해 별도의 작업 공간을 만든다.
2. 브랜치에서 에러가 발생한 버전을 이전 버전으로 되돌리거나 삭제한다.
3. 브랜치는 완전하게 독립 되어있어서 작업 내용이 master 브랜치에 아무런 영향을 끼치지못한다.

기본 브랜치
초기 상태를 나타내며 일반적으로 프로젝트의 가장 최신 버전 또는 배포 가능한 안정적인 코드를 포함

기준점
다른 브랜치가 파생되는 기준점으로 사용됨

### Branch Commend

git branch  - 브랜치 목록 확인
git branch -r  원격 저장소의 브랜치 목록 확인
git branch <브랜치 이름> 새로운 브랜치 생성 ( 생성만 이동 X)
git branch -d <> 브랜치 삭제(병합된 브랜치만 삭제 가능)
git branch -D <> 브랜치 삭제 (강제 삭제)

git switch <다른 브랜치 이름> 다른 브랜치로 전환
git switch -c <> 새 브랜치 생성 후 전환
git switch -c <> <commit ID> 특정 커밋에서 새 브랜치 생성 후 전환


##  주의사항

1. master 브랜치와 feature 브랜치가 존재
2. feature 브랜치에서 'article.txt'를 생성
3. git add 하지 않고 git switch master 실행

### 브랜치 시나리오

git log --oneline --all --graph
사용하여 브랜치 확인 가능

# Git Merge
두브랜치를 병합

git merge <병합 브랜치 이름>

1. 수신 브랜치 확인하기
   - HEAD 가 올바른 수신 브랜치를 가리키는지 확인
   - 병합 진행위치는 반드시 수신 브랜치에서 진행되어야함

2. 최신 commit 상태 확인하기

Merge 종류

1. Fast-Forward Merge
2. 3-Way Merge

### 빨리 감기
브랜치를 실제 병합하는 대신 현재 브랜치 상태를 대상 브랜치 상태로 이동시키는 작업 
가장 최신으로 가져오는 작업

### 3way Merge
공통 조상과 나누어진 2개 총 3개를 비교해서 하나로 합친다.

머지 이후 다른 터미널  esc - : - wq (저장후 나가기)

충돌 시

Merge Conflict

충돌시 변경 점 모두 수정하고 add . 하고 git commit 만 입력후 esc : wq 

# Git Workflow

Feature Branch Workflow
권한을 공유 받는 방식


# Forking Workflow

gir remote add upstream [원본 URL]