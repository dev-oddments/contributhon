# contributhon 기록 (2018. 08. 16 ~)
## > 개괄적인 내용
KOSSLAB(선릉역) - 정기모임 많으면 일주일에 1번 // 첫모임 8월 20일(화) 7시 반

Mission : 중간단계를 둬서 스텝을 밟아 어느정도 수준까지 이끌어갈 수 있도록

[kosslab-kr](https://github.com/kosslab-kr)

Offline & Online 섞어서 // [info](https://docs.google.com/spreadsheets/d/19sMYJYv8EdVRTaVZC6lUULdCs5KfiHM5M-_PnnbQJUU/edit#gid=0) / [chatroom](https://gitter.im/uftrace/uftrace)

** 작게나마 다른 환경에서의 trouble shooting
## > 앞으로 할 일
- 프로젝트 소개문서
- 개발환경 구성문서
- 커밋 분석 보고서
- 컨트리뷰션 진행상황
- Issue 등록
- Perf contribution
```
1. Git/Github 협업방식 훈련
- Git/Github 의 기본실습
- 협업 시 사용하는 명령 및 이슈 해결법 이해 (rebase 등)
- 오픈소스 개발방식 이해

2. uftrace 프로젝트 이해와 정리
- 프로젝트 명
- 분야 및 한 줄 정의
- 사용언어
- 주요 feature 에 대한 시나리오 1 개
- 총 라인 수, 폴더 나뉜 구조(depth 2-3)
- 소스 → ( 컴파일 / 세팅 ) → 실행 과정

3. 선정된 프로젝트 개발환경구성
- 개발 및 테스트 환경 구성 : IDE 및 편집기와 debugging 툴 세팅
- 컴파일 / 실행 테스트 : “hello world” 및 임의 내용 포함 테스트
- Git 개발 환경 구성 : local, remote repo, upstream 구조 잡기

4. Linux 기반 Tracing 도구 개발을 위한 스터디
- ELF, PLT/GOT, x86 calling convention 등 background knowledge
- uftrace 주요 기능에 대한 소스리딩(분석)

5. 시나리오 기반 소스 분석
- 하나의 기능을 선정해서 그것이 실행되는 과정을 분석
- 그와 관련된 class, data structure, function, call-graph 등을 분석

6. 프로젝트에 기여하기 (Contribution)
- 버그/리팩토링/minor feature PATCH 거리 수색하기
- 분석한 시나리오를 바탕으로 다각도로 프로그램을 실행하며 분석적으로 사용한다.
- 분석한 시나리오를 바탕으로 소스의 리팩토링 가능여부를 살펴보며 분석한다.
- 이외의 다각도 시나리오로 이용하며 부족하거나 필요한 기능에 대해서 고민하고 구현해 본다.
- pull-request 전송
- pull-request 전에 코드컨벤션 확인 및 테스트를 필수적으로 한다.
- 완성한 다양한 수정사항(commit)을 해당 프로젝트에 pull-request 한다.
```
## > 소개
namhyung님 - 메인테이너
## 1. 박한범 멘토님
작년엔 참가자였지만 32bit 대응을 하는걸로 지금은 커미터가 됨

뭘 빡 하겠다 하기 보다는 장기적으로 편안하게 생각하는게 도움이 된다

- uftrace : 트레이싱을 해주는 툴 / C, C++, Go, Rust 'Hello World' 트레이싱 결과 그래프 출력 - Go에서는 functioncall이 1000번은 일어나야함..

### Dalvik 분석하기
소스코드 라인이 분석할 수 없을정도로 많다.

cscope, ctag를 과거엔 썻음 - 답이 없다..

Android os에서는 hello world 찍는데 11만번의 functioncall이 일어남

LLVM, GCC등에 대해서도 더 잘 알고싶다는 생각에 기여를 하고있음

uftrace라는 툴을 이용해서 개인의 목적을 이루는 것 또한 좋은 기여활동이라 할 수 있다.

2016년에는 Rust로 참여했었다. PR을 날렸는데 하나하나 고액과외를 받는 것 처럼 친절하게 설명해주었다.

비영리 활동이지만 가치있는 일
## 2. 송태웅 멘토님 - taeung@kosslab.kr
### 1) Opensource Software Development - 오픈소스 개발 방식의 이해
각종 오픈소스(OS, framework, lib)의 기술내용이 아닌 개발 매커니즘(오픈소스 개발 방식)

How to develop with Git? - Git은 히스토리 관리(log : 왜 했는가?, 뭐가 달라졌는가?)

Git은 Collaboration Tool - 협업을 기반으로 어떻게 생각할 것인가?

rebase, blame 등에 대해서 협업으로서의 상황상의 배경을 알아서 이해해야 함.

rebase를 쓰고있는거 자체가 협업을 엄청 하고있다는 증거

rebase : upstream을 쫓아가는 것 - 충돌나는 시점(fork 떠서 clone을 받고 Patch를 했는데 그새 다른게 merge가 되어있는 상황 -> upstream의 base를 교체하는게 rebase) // 상황속에서 겪어봐야지 그걸 진정으로 이해할 수 있음

Commit 단위로 개발을 진행?
#### utfrace needs
gcc에 -pc옵션을 주면 각각의 함수 중간에 ncount functioncall 하는것 처럼 출력할 수 있음

uftrace <- functioncall 추적 가능, 코드의 호출 등을 볼 수 있음 // 알고리즘을 짰을 때 제대로 내 의도대로 돌아가고 있는지 확인 가능

callback이 많은경우 혹은 event handler가 많을경우 <- 소스코드만 읽는거롤 이해가 안되는 경우가 많다.

kernalfunction <- 인자에 따라 달라질 수 있으므로

결과를 json으로 뽑아내서 chrome으로 볼 수 있음 // chrome://tracing

#### namhyung님
커널에 기여 한국 top, 해외에서도 상위권

소스가 오픈이 되어있는가와 오픈소스는 다르다. 리뷰와 discussion이 있는가 없는가가 오픈소스가 살아있는지 여부를 판단할 수 있는 기준

커널쪽 내공을 가지고 uftrace를 프로페셔널하게 운영하고 계심

Honggyu Kim <- advanced한 testcase를 잘 뽑아내시고 하드한 테스트를 잘 해주심(ex-etherium 등), 다른 툴에대해서도 조예기 깊으심

가치를 위한 코드를 만드는 것 = 실질적인 니즈에 따라 구현
### 2) 오픈소스 프로젝트 uftrace: Pull request / Review 과정 예시
> 기여 종류 : 1. pull request / 2. documentation
#### pull request
내가만든 커밋을 제출하는 것(남의 프로젝트일 경우) - github 입장에서는 issue와 마찬가지로 게시글 하나 올라오는거랑 같음

ex) Support a float time value for trigger

내가 만든 코드에 대한 Description의 전략도 굉장히 중요하다 - 이런것에 대해 많이 배울 수 있을 것 // 어떻게 전달하고 설득할 것인가?, 왜했는지 적는 것

하지만 리뷰에대해서 어떻게 받아들이는지도 중요 - 쪽팔려 할 것인가? 아니면 배우는 자세로 계속 해나갈 것인가? // 버전(리뷰수)이 올라갈수록 명예롭게 생각해야 함
#### Issue - pr이랑 생긴건 비슷하다 but 버그리포트
버그에 따라서 critical 라벨이 붙은건 더 빨리 처리해야 한다는걸 알림

문제상황이 만들어졌던 라이브러리는 뭔지 알려줘야 함

FYI <- for your information

메인테이너가 만든 Issue -> Review 라벨이 달림 근데 왜? 보통은 rfc를 달아서 논평을 요청하는 것

### 3) uftrace 실습
sudo apt install libelf-dev

sudo dnf install elfutils-libelf-devel

git clone https://github.com/namhyung/uftrace.git

cd uftrace

make

sudo make install

[tutorial]() - nmap // 

** 스케쥴링이 언제되는지도 알 수 있음
## 3. 김재중 멘토님
bsp(리눅스 드라이버) / 현재는 차량용

리눅스 커널은 비쥬얼하지 않고 올드하고 모든 패치가 메일로 이루어진다. 모든것이 텍스트로 이루어짐 // 물론 네이밍이나 룰 등이 있음

너무 쫄지마라 

***
- 명령어를 치면 크롬으로 트레이싱 결과를 보여주도록 하는 옵션

