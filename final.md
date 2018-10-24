# Uftrace 결과보고서
> 2018 08.16 ~ 2018 10.25

## 주차별 강의 정리
- [week1](https://github.com/dididy/contributhon/blob/master/record_day1.md)
- [week2](https://github.com/dididy/contributhon/blob/master/record_day2.md)
- [week3](https://github.com/dididy/contributhon/blob/master/record_day3.md)
- [week4](https://github.com/dididy/contributhon/blob/master/record_day4.md)
- [week6](https://github.com/dididy/contributhon/blob/master/record_day6.md)

## 학습 내용
- git rebase
- Linux Kernal 개발을 위한 git 사용법 
- Uftrace 사용법
- Uftrace 내부구조(internals) 
  - gdb활용
- 오픈소스 기여 : pycharm-kr [#1](https://github.com/traff/pycharm-kr/pull/1) - merged
- yocto(poky - bitbake) 사용법

## 기여하고자 했더 것
- `tests/` 폴더 내부 테스트 파일 손보기
- 초보자를 위한 Uftrace 한글 문서 작성 
- yocto 패키지 내부의 uftrace 버전 갱신

## Update yocto package version of Uftrace(0.8.3 to 0.9)
<img width="727" alt="2018-10-23 11 16 16" src="https://user-images.githubusercontent.com/16266103/47368836-5aab4f80-d71d-11e8-8bbd-096c4434b3c7.png">

### Build process
```
$ mkdir something
$ cd something
$ git clone git://git.yoctoproject.org/poky
$ git clone git://git.openembedded.org/meta-openembedded 
$ cp -r meta-openembedded/meta-oe/recipes-devtools/uftrace poky/meta/recipes-devtools
$ cd poky
$ source oe-init-build-env
$ bitbake uftrace
```

### Build new version of Uftrace
> Still in progress

### [How to submit patch](http://www.openembedded.org/wiki/How_to_submit_a_patch_to_OpenEmbedded)

## 후기
```
  컨트리뷰톤을 통해 C/C++ 함수 트레이싱 툴인 Uftrace의 개념과 내부구조를 접할 수 있었고 오픈소스에 기여하는 방법을 알게되었습니다. 비록 Uftrace에 PR을 날린건 아니지만 배운 내용을 바탕으로 PyCharm 공식 한국어 번역 프로젝트에 PR을 넣어 merge가 되었고 별거 아니긴 해도 뭔가 해냈다는 생각에 뿌듯함을 느꼈습니다. 이때 제가 느꼈더 뿌듯함이 오픈소스를 돌아가게 하는 원동력이 아닐까 생각됩니다.
  
  내공이 부족해 Uftrace 리포지토리에 올라 와있는 이슈를 처리하거나 새로운 기능을 추가하는 등의 기여를 하지 못했던건 아쉽습니다. 잘 쌓아올려진 단단한 건축물 같은 느낌이라 제가 뭔가를 건들인다는게 부담스러웠습니다. 사실 소스에 대하 이해조차 잘 되지 않는 상황이라 어쩔 수 없었던 것 같습니다. 하지만 [안이수](https://github.com/memnoth)님의 도움으로 Yocto 패키지 내부의 Uftrace 버전 갱신이라는 주제로 기여하겠다는 방향을 잡았고 현재 명확한 결과를 낸건 아니지만 이작업만큼은 길게 걸리더라도 해보겠다는 목표의식이 생겼습니다. 
```
