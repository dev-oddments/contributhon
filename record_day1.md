# Contributhon 1회차(8/20) 정리
> 커널패닉으로 atom에 정리해놓은게 날아가서 다시 작성해봄

## Git
git log
- 지금까지한 4개의 commit들을 확인

git shortlog
- 간단한 형태로 커밋리스트 출력

git status
- 상태와 브랜치명을 확인(기본은 master 원격 저장소는 origin)

git commit -sm "something"
- 서명과 함께 커밋함(사실 용도를 모르겠음)

gir remote add origin URL
- Github 원격 저장소 등록

git commit --amend
- 직전에 커밋한 내용 수정(하지만 직전 커밋내용을 이미 push한 상황이라면 --force를 써야한다. 로컬에서 push전에 수정하기는 괜찮지만 공동작업할때는 비추)

git reset
- add한거 취소

git reset HEAD~1
```
HEAD는 현재 브랜치(브랜치에 담긴 가장 마지막 커밋을 가리킴)를 가리키는 포인터
Index는 바로 다음에 커밋할 것들

WorkDIR / Index / HEAD || <- workflow - 프로젝트 스냅샷 지속적으로 저장
  WorkDIR -> Index : stage file ~ git add
  Index -> HEAD : commit ~ git commit
  HEAD -> WorkDIR : checkout the project

RESET의 역할 : 1) HEAD의 이동(--soft) / 2) Index update(--mixed) / 3) WorkDIR update(--hard)
```
git checkout
- branch 스냅샷을 기준으로 WorkDIR을 안전하게 다룸(reset --hard는 파일보장이 안됨), HEAD의 포인터가 아닌 HEAD 자체를 옮김 

git fetch
- 원격 저장소의 최신이력 확인 가능 'FETCH_HEAD'이름으로 checkout 가능 

upstream?
```
리모트 트래킹 브랜치를 로컬 브랜치로 Checkout 하면 자동으로 “트래킹(Tracking) 브랜치” 가 만들어진다 (트래킹 하는 대상 브랜치를 “Upstream 브랜치” 라고 부른다). 트래킹 브랜치는 리모트 브랜치와 직접적인 연결고리가 있는 로컬 브랜치이다. 트래킹 브랜치에서 git pull 명령을 내리면 리모트 저장소로부터 데이터를 내려받아 연결된 리모트 브랜치와 자동으로 Merge 한다.
```

git rebase

git rebase -i root

git reabse --continue

git blame [FILE]
- 누가 어느라인을 수정했는지 파악

git show [commitID]
- 그 당시 커밋정보 확인


## 궁금 한 것
- rebase는 포크받지않은 원래 저장소로부터 fetch받은 후 진행되야 한다는 것은 이해함. 그럼 rebase시 commit 목록에 내가 fetch전에 작업했던 commit이 있는가? 그렇다면 fetch전 작업 내용을 fetch이후 commit으로 만드는게 rebase의 목적인가?
