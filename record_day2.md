# Contributhon 2회차(8/27) 정리
## rebase 
git remote add origin [URL] // 
git remote add upstream [원본URL]
- github 원본 리포지토리 등록

git fetch upstream master
- .git 파일에 내부적으로 가지고 있음

git rebase upstream/master
- rebase 진입 

> 수정 후 git add

git rebase --continue
- rebase 완료

## 원본 리포지토리에 포크받은 이후에 변경사항이 생겼을 경우 
- remote로 add로 원본리포 URL 추가
- fetch로 원본리포지토리 변경사항 적재
- rebase로 

rebase시 conflict <- 같은 파일내에 수정이 이뤄진 경우 

## record 과정
[[1]](https://www.dropbox.com/s/dl/fyz7q2onl7ea422/uftrace_internals.pdf)

[[2]](https://schd.ws/hosted_files/osseu17/52/Good_bye_printf_hands_on_tutorial_uftrace_function_graph_tracer_C_C%2B%2B.pdf) - line by line

## 다음 schedule / contribute 할 수 있는 것 생각 

- info dump 등의 명령

- documentation 에 빠져있는것(option 설명이 없는 것)

- example 같은거 

- 내가 찾아나가는 과정!
