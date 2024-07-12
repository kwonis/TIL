# Git revert & reset
## revert
특정 commit을 없었던 일로 만드는 작업
```
git revert commit id(4개에서 5개)
```
- 재설정
- 단일 commit을 실행 취소 하는 것
- commit은 남지만 내용은 삭제 후 새로운 결과만 저장하는 commit으로 저장 

이후 Vim 화면으로 넘어가짐
-이유 commit이 생성 되므로 메세지를 써야하기때문에 

맨 처음 줄에 commit 추천 해준다.

Vim을 빠져나가거나 수정 하는 방법
- 입력모드(수정) 전환 방법 (i 클릭)
- 명령모드(저장 및 나가기) (esc)->(shift + ;)->(w(저장)q(나가기))
## 왜 Commit 을 남겨 둘까?
commit을 없애면 push 불가 그리고 팀원들과의 협업에 문제가 생김.

### 추가 명령어
```
/여러개 삭제 가능
git revert commit id commit id commit id

/범위 지정
git revert commit id..commit id

/Vim을 열지않음 
git revert --no-edit

/commit 을 진행 하지않음
git revert --no-commit 
```
---

# Reset
특정 commit으로 되돌아가는 작업
```
git reset [옵션] <commit id>

옵션(기록을 어떤 영역에 둘 것이냐)
--soft (staging area 중간 지역으로)
--mixed(working directory에 남김)
--hard(아예 삭제)
```
- 되돌리기
- 과거롤 되돌리는 행위
- 시점 이후 commit 모두 삭제

reset 이후 복구 하려면?

git reflog를 통해 확인 후

git reset --hard  를 통해서 복구 가능

### 부록
- 파일 내용을 수정전으로 되돌리기
  
  git restore(Modified 상태의 파일 되돌리기)지우는게 아닌 덮어쓰기 사용 후 복구 불가능

- Staging area에 올라간 파일을 Unstage하기
```
git rm --cached 이름
중간에서 처음으로   (git 저장소에 commit이 없는 경우)
git restore --staged 이름(commit이 존재하는 저장소에서)
```

# commit 수정 (직전)
- commit 메시지 수정
- commit 전체 수정 
```
git commit --amend
명령어는 똑같다. 타이밍에 따라 달라진다.
```
commit id 가 변하기에 협업중이라면 혼자 사용하지 않아야 한다.

# github 프로필 만들기
1. 프로잭트 협업
1. 개인 포트폴리오

