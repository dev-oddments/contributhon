# KOSSCON 2018 (2018. 08. 16)
## > 참가동기
contributhon 개회사가 오늘 5시 30분부터 진행되게되는데 어떤내용이 나올지 궁금해서 행사장에 미리 도착하여 KOSSCON도 참여하게 되었다.

## > 오픈소스가 어떻게 산업을 바꾸는가? - 카카오 공용준 상무(클라우드)
오픈소스의 시작 <- 1970년대까지만해도 소스는 공개하지 않는게 원칙 But 리처드 스톨만이 HP가 프린터 지원중단해서 빡쳐서 시작하게 됨

리눅스를 기점으로 Unix(슈퍼컴퓨터)는 점유율이 급격하게 하락함 - 리눅스의 안정성과 속도는 증명 됨

Pnetagon이 내년부터 오픈소스 제작에 큰 지원을 시작함 - Mil-OSS

뱅킹시스템 전체 및 분산처리 오픈소스 - openbankIT, Apache Fineract

TDD(원래 개발하는 사람이 다른부서로 가도 시스템이 돌아야함) / DevOps(Ops가 없는 것, 인프라를 운영하는 사람은 점점 줄어든다) / Cloud Native(모든것들을 API로)

BDFL is also human, has feelings, has ages, sometimes want to retire though the name is 'For life' / Community : United we stand, Divide we fall!


** MariaDB는 정말 많이 쓴다고 함

## 1. 웹의 미래와 현재 - Prograssive Web App (Track2) : 장기효(캡틴판교)
웹앱의 새로운 형태 / 기존의 웹사이트가 어떻게 진화해가고 있는가?

### 소개
모바일 앱과 같은 경험을 주는 최신 웹 앱

앱아이콘, 앱아이콘 설치 배너, 모바일 푸시, 오프라인 경험 제공

HTML, CSS, JS로 모바일 앱과 같은 웹 앱을 구현

"높은 사용자 경험을 제공하기 위한 웹 앱의 진화"

### 등장배경
모바일 시장의 폭발적인 성장

모바일 웹 보다는 모바일 어플리케이션

모바일 앱 영역을 커버하기 위한 시도들 - Hybrid App, React Native

Offline Web의 필요성
### 특징
Responsive

App-like

Discoverable

Engageable

Push

Connectivity(오프라인 웹앱)

Security
### 적용사례

### 제작기술
크게 두가지가 있다.
#### 첫번째
menifest.json - 웹앱에 대한 메타데이터
#### 두번째
Service Workers: client-side JavaScript proxy / javascript가 백그란운드에서 proxy 역할을 하는 형태

### 지원 브라우저
PWA는 브라우저 종속적

FF, Opera, Chrome, Safari 등 지원하고 있음
### 참고자료
web fundamentals
[google codelab](https://codelabs.developers.google.com/codelabs/your-first-pwapp/#0)
## 2. Tox : 차세대 메신저 엔진 : 조남수
p2p 기술을 이용한 인스탄트 메시징 기술(c로는 구현이 되어있음)

C로 개발되어 있는걸 Rust를 이용해서 다시개발하고 있음

Rust에 대해서도
### Tox 메신저 엔진과 클라이언트
라이브러리 형태로 제공 + API

엔진에 UI를 입힌게 Tox Client
### Tox client의 기능
메시지 교환 / 그룹 채팅방 / 화상 통화(RTP) / 파일 전송
### Actual Tox Client
윈도우, 리눅스, 안드로이드, OS X 등 클라이언트가 이미 있음
### Introduction to Tox - 분산 해시테이블(중앙에 서버가 없음 - 블록체인과 같음) / 해킹으로부터 안전한 메신저를 만들어 보자 - 보안성 탁월 / 가성비 우수(서버가 많이 필요하지 않음)
P2P commuinication using DHT(DHT를 사용시 2억명까지는 일반적으로 커버가능)

Data Encryption of end to end

Supports both IPv4 and IPv6

Can run even if node is behind NAT

Upgrading is in progress
### Distrivuted Hash Table
개념은 간단하다. 내가 테이블의 일부를 가지고 있고 이를 끊이없이 교환함
### DHT node
- PublicKey : used as hash PublicKey
- Socket address : IPv4 and IPv6 socket address
- clone_node_list : array of node<PublicKey, SocketAddr>
- Bootstrap : public bootstrap node already exists. / Request node list based on my PublicKey / Maintain close_node_list
- Response containing node list from request by other node\
### Secure communication - 각각의 대화기록이 서버에서 관리되지 않기 때문에 보안이 탁월홤
- PublicKey, SecretKey.
- Nonce.
- TOXID.
- There ad no centralized servers.
### Implementations fo Toxcore.
- TokTok [github](https://github.com/TokTok/c-toxcore)
- Tox-rs - written in Rust [github](https://github.com/tox-rs/tox)
### Future of Tox
- At first, it aimed replacement of Skype.
- Should be adopted to Mobile environment.
- Have to solve offline message problem
- Trying to extend protocol standard to accommodate multi-device
- Can replace current messaging system for costeffective reason
### Useful links
[표준규약](https://github.com/TokTok/spec/blob/master/spec.md)
### Tox의 목표는 뭐냐?
간단하면서 안전한 메신저가 되겠다

세상에는 이미 너무나도 많은 메신저가 있다 -> configuration이 없는 메신저 엔진을 만들려고 한다
### Toxcore written in Rust
- Why Rust
- Maintaining current c-toxcore needs much efforts
- Light weight engine is needed to reside in mobile device(현재 톡스코어는 그대로 모바일에 올라가기에는 무겁다)
### Why Rust
- Version 1.0 was released about 3 years ago.
- Memory Safety.
- Thread Safety.
- Cost free abstraction.
- Functional programming paradigm.
- System programming like using high level language.
### Data race
- Traditional problem in multi-thread programming
- Solve using Mutex, Semaphore, ...
- 100% up to the human to guarantee safety.
- Sometimes it demands much debugging.
- Sometimes it requires abandoning codes almost done.
### Memory safety
- Ownership
- Borrowing
- Cloning, Copying
### Thread safety
- Two thread can't have write access to one resource simultaneously.
- Two case: Many read access to one resource / Only one write access to one resource
- Checked by compiler at compile Sometimes
### Cost-free abstraction
- Rust is a strong typed language.
- Provide powerful type System
- Unlike other languages, codes written in Rust are compiled to direct machine language not much depending on runtime environments.
- No garbage collector.
### Functional programming using Rust
- Iterator(순환자)
- Clojure
- Powerful combinators
### Rust acts like a High Level language
- It don't depend on garbage collector.
- Unlike C/C++, code can be written without using pointer.
- Human can read codes easier than C/C++
- Rust supports convenient TDD(테스트 자동화)
- Cargo provides powerful developing environments.(intelliJ compatible)
- crate.io repository(라이브러리 다운받아서 사용가능)
### Official comments
Rust project의 목표 -> 효율적인 시스템 프로그램을 만들겠다. / C는 안전성이나 동시성, 자원에 대한 제어도 알아서 해야했음 이를 보완할 수 있는게 RUST

Rust는 100%를 추구하지 않는다 실용성을 원한다 실용성을 위해서 다른걸 희생할 수 있다.
### Useful links
520 - rust vs comparison

why i'm dropping rust

ruskt-lang.org/ko-KR/documentation.html

rust-doc-korean
## 3. Implementing private blockchain - 이준범(카이스트 전산학부 석사)
It-chain : Customizable and Lightweight Blockchain
### It-chain
중소규모 커뮤니티에서 유연하고 자유롭게 이용 가능한 '경량 맞춤형 블록체인 엔진'개발 및 블록체인 코어 공부

핵심 서비스의 모듈화를 통해 목적에 맞게 쉽게 교체 가능 하도록 개발

지역 특화 토큰 플랫폼 / 중고 물품 거래 플랫폼 / 소상공인을 위한 거래 플랫폼 -> It-chain engine
- State Transition Function
- 시나리오 - Network 구성 : one leader
- Submit Request - Invoke transaction / Query
- Forward to leader
- Crate Block and Start Consensus - simulation
- Add block and update State
### Architecture
요구사항
- 손수비게 수정 확장
- 오픈소스
- 중앙관리자 없이 p2p 구조
- 기본적인 블록체인 긴으 지우너 - block storage 컴포넌트 / authentication 컴포넌트 / consensus 컴포넌트
- consensus
모든 노드가 서로의 노드를 알고있음 gIPC를 이용해 연결(합의과정이 빨라짐)
### Block, Transaction
중간에 있는 블록을 수정하기 굉장히 어려운 구조 - 위변조에 강하다

yggdrasil라이브러리 - 블록체인을 저장할 수 있음 / Header와 Data로 구분 / Header에는 블록에 대한 메타정보가 저장

- Transaction - ICode실행 요청 / JSON-RPC

Block Seal 값을 Key로 Value 조회 / Last Block으로 부터 순차적으로 조회가능
### Consensus
단일 데이터값에 대한 합의

블록이 서로 다른블록을 저장하면 안됨

신뢰할 수 있는 노드가 들어있더라도 나머지 노드들은 잘 저장할 수 있도록 함

비잔틴 장군 문제 - 성을 함락할 때 3명이 필요한데 장군들 중 배신자가 있다면 서로 신뢰할 수 없게됨 - PBFT : 분산 시스템이 있을 때 결과값을 맞추자는 알고리즘
### IVM(Icode Virtual Machine)
= It-chain 스마트 컨태랙 deploy, invoke 수행
- World State DB 관리
- Docker 컨테이너 기반의 독립적인 환경 제공
- SDK를 통해 다양한 언어 사용 가능
## 4. Backend.AI 소개 및 튜토리얼 - 오픈소스 머신러닝 인프라 프레임워크 // Mario Cho : m.cho@lablup.com
알파고나 인공지능에 엄청난 컴퓨팅 연산자원을 사용하게 됨
### 문제 의식 : 왜 이렇게 힘들어?
오픈소스와 클라우드의 발달 - 정말로 AI 하기가 쉬워졌을까?

Tensorflow - 6주마다 버전업 : 호환성 고려 x
### 우리에게 필요한 것
쉽게 / 함께 / 빠르게 / 어디서나 / 값싸게
### 지원 프로그래밍 언어 - docker hub에 컨테이너 이미지 오픈 해놨음
python php, r, node.js, js, tensorflow, haskell, typescript, rust, go 등
### 개념도
다양한 자원을 분산해서 만들어 줌

- 개인 조직 사용자 / 응용 서비스 및 애플리케이션 - 클라우드, 웹 서비스, 모바일 및 IoT 장비
- Backend.AI 플랫폼 - 오토스케일링, 보안격리, 버전관리, 언어별 SDK, 자원할당, 모니터링 / 클라우드 인프라(IaaS) - AWS, gCloud / 온.프레미스 클러스터
### 포지셔닝
- 개발자를 위한 사용자 인터페이스
- GPU를 사용하는 다양한 도구
- 오케스트레이션 계층
- 가상화 솔루션 및 클라우드 서비스
### Backend.AI 사용 시나리오
- GPU가 없는 랩탑을 들고다니며 딥러닝 AI를 개바랗고 싶을 때
- 사내 고성능 GPU서버 1대를 여러 연구원이 공유하면서 쓰고 싶을 때
- 망분리 적용된 사내 GPU 서버를 조직 단위로 유연하게 공유하고 싶을 때

** 아무리 오픈소스라고 한들 노하우는 전달하기 힘들다 - 컨설팅 모델의 존재이유
## 5. webOS OSE의 Native App & Service 개발환경 - 고석하(LG전자 - sh.ko@lge.com)
발표 내용이 완전히 임베디드 관련하여 이야기 할 것 같다
### Background
webOS 올 봄에 오픈함 / 개발자사이트 & github - 가이드를 확인할 수 있음

경험담 및 수기정도로 들으면 될 것 같다
### Developer framework
webOS자체가 TV와 뗄레야 뗄 수 없음 -> Native C++로 이미 짜여있음(웹앱, 네이티브 병행)

- service - Application 혹은 다른 service의 요청에 대한 응답 / application - system bus를 통해서 통신
- built-in / installable - Platform에 미리 탑재되는지, Store등에 의해 install 되는지
- http://webosose.org - Luna bus와의 연결, API 접근 권한 설정, Built-in, Installable web Application
### 오늘 할 이야기
- installable - Native app(Qt), Native service(Qt, C/C++)
- How to make NDK - Libs & header, Toolchain, other tools
- webOS CLI - For packaging & installation
- 그래서 코드 자체를 다루지는 않음
### Luna Bus
외부에서 서비스나 어플리케이션을 만들 때 무조건 알아야 함
### LSM - wayland server로 동작 // 개념적으론 알아야 하는 부분
- Window management
- Input event routing
- Composition among App windows and System UI elements
### Native Development Kit
Development environment
- Yocto
- OpenEmbedded : Bitbake / Metadata : struectured collection of "recipes"
OE Cross Toolchain Generation
- Target device
- Build Machine
Generate NDK Using OE
- bitbake webos-image-devel -c populate_sdk
- bitbake meta-toolchain-qt5
- Make your own recipes for NDK
### Contents of NDK
- whole sysroot libs, ehader, package config files etc
- GCC 6.2.0(C++14 support), binutils, other tools
- Linux environment variable setup file for cross compile
- Qt tools(mkspecs, qmake, mooc, uic, rcc, ...)
### Example
- app / app + native - service 단독 설치는 불가
- Service ID는 app id의 subdomain - com.example.native, com.example.service
### Native Service
- 소스 작성 부분은 built-in service와 동일 - Luna bus registration
- 다만, ls2 conf, role, API permission 등 파일 불필요 - appinstalld가 자동 생성
- systemd unit configuration 팡리 불필요
- services,json firle for packaging
### Native app
- Luna bus, SAM, LSM에 각각 등록을 해야 하는가? : 해야한다

** webOS 플랫폼 자체가 오픈되어있고 오픈소스를 끌어다쓰는 경우도 많기 때문에 다양한 부분에서 개발을 해볼 수 있다.
gtk는 덩치가 커서 qt를 사용함
