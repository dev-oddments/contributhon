# uftrace 3주차

## Linux Kernel 개발을 위해 익숙해 져야 할것들.
> 사례 여러가지 살펴보기
virtual file system으로 되어있어서 상황에따라 다

의도 : contribution 꺼리를 찾아야 함 이것을 유도하기 위해서 이번 시간을 가짐

리눅스 드라이브에 컨트리뷰션을 하는 사람임 // 차량용 AVN(카오디오 등)의 리눅스 드라이버 개발 - 김세중(linux contribution 1년차)

PPT 만들때 고민을 많이 함 // 모인 사람들이 굉장히 다양함

커널쪽 contribution 내용들 <- 이론적인 내용들이 없음

Kernal Contribution 하게된 이유 : 회사생활 하면서 자괴감(발가벗은 상태에서 밖에 나갔을 때 나를 어떻게 설명할 것인가?)


> 커널쪽 git이 어떻게 운영되는가?

### 익숙해져야 할 것들 #1
Vi / Emacs 등의 Command 환경 && terminal에 default로 익숙해 져야 함
### 익숙해야져 할 것들 #2
```bash
git commit --ammend // version2나 뭔가 추가해야 할
git apply ~/where/to/*.patch // index쪽에 diff
git format-patch -1 -o /where/you/want // ptach파일에 괜해서 일일이 손으로
git send-email --annotate --cover-letter -to @gmail.com *.patch // --cover-letter : 0번패치를 만들어줌, 시리즈에 대한 기본적인 설명을 적음
git send-email --to-cmd ./scripts/get_maintainer.pl /where/to/*.patch // --to-cmd 쉘스크립트를 이용해서 자동으로 보내줌
```
github와 다르게 일일이 다 손으로 함
### #3 Linux Kernel Mailing list
linux newbie를 보면 하루에 메일이 수천개씩 쏟아짐
* linus torvalds shut up <- patch를 넣고 소리를 안나는 문제가 생김
  * lkml/2013/7/15/329이거 번역해보자

* git에 패치 반영한느 방법 -> git am
### #4 영어
* 다른 사람들의 작성한 commit들이 좋은 reference
### #5 패치만들기
* 패치를 보냈는데 리뷰를 통해 수정할 부분을 지적받은 경우 -> V[number]
* 패치를 만들었는데 신규 기능 추가
  * RFC(Requests for comments) prefix
  * 가끔은 일단 패치는 만들어서 수정되는건 확인했는데, 나도 확시닝 없네.
* Version에 따른 patch내용의 변경사항 업데이트 하기
### 실습 & Q&A
구글림 -> 김남영님 blog : linux patch
> 오늘 할 실습 : 예외케이스

* naming -> subsystem ex) usb: gadget: acm: Add commnet

* coding rule <- 검사하는 script파일이 따로 존재함
* get_maintainer.pl <- 보내야할 메인테이너 <- 근데 이렇게 잘 안함 그냥 메일링리스트로 보냄

* 공용체, 파일시스템, 동기화 등등 너무 많은 진입장벽.. <- 시스템 프로그래밍 많이 해봐라! / linux의 sysnode를 잡아다가 udev, 소켓통신 등등의 유저프로그램
* 마우스를 클릭했을 때 - 하드웨어 인터럽트// 이게 정말인지 확인하는 것 -> 워크 큐
* lsusb, ps 등등 이 모두 system programming임
* linux device driver는 워낙 많은 예제들이 이미 공개되어 있음
* uftrace로 리눅스 커널 따라가보기 <- 이런부분에서 uftrace가 괜찮음, 시작점 잡기도 좋음
* linux kernal 공부를 할 때에는 길을 잃으면 안됨(자신의 주제를 확실하게)
* lsmod | grep
* insmod
* sudo insmod work.ko wq_type=1// 인자값을 줄 수 있음
* reference counter
## 커널 예제 중 가볍게 다가갈 수 있는
> uftrace --force /bin/rm -f a // unlinkat()이 가장중요 <- system core를 불러옴
> vim src/rm.c //에서 main확인하고 마지막에 rm이 있고 remove.c에 rm이 정의되어있음
> grep unlinkat
uftrace user를 포기하고 library, kernal은 볼 수 있음
> df -h -T  본인 root에 filesystem이 보
### 함수 트레이싱
```
touch a
> sudo uftrace --force -K 20 /bin/rm -f -a # -K옵션은 depth를 주는 것
user든 library든 kernal이든 함수의 연속임
unlinkat은 시스템콜


#include <stdio.h>

int main()
{
  printf("hello\n");
  fflush(stdout);
}

> gcc -pg hello.c
> uftrace ./a.out
> sudo uftrace -K 2 ./a.out
해보면 sys_write();가 어디서 눌리는가 즉각적으로 불리지 않다는걸 알 수 있음
> sudo apt-get install silversearcher-ag // grep보다 훨씬 빠름
callback이 2~3계층으로 되어있으면 힘듬
> ag ext4_unlink
ext4_evit_inode()
> ag "\.evict"

> ls /sys/fs // 이 아래에있는 파일은 일반 파일이 아님
> mount | grep sys
bpf -> 돌고있는 커널에 주입하는 것(새로운 function 추가가능)

> bpf-tools prog Show
> ls /sys/fs/bpf/x1
욜러 갈 때 uftrace를 쓰면 진입장벽을 확 낮출 수 있음

소스코드로 직접 찾아가는건 한계가 있다. callback이 많을 때 착각할 수 잇음
반면 uftrace는 순식간에 파악가능
그리고uftrace는 .data파일에 그당시 명령어와 컴퓨터정보 그리고 커널정보등을 담고있기 때문에 이를 공유하는식으로 문제를 전달할 수 잇음
```
## script기능
합수가 시작했을 때 시작을 기록 종료했을 때 종료를 기록 <- 이 매커니즘이 uftrace
```c
#include <stdio.h>

int main(){
	int n = 20;
	long i, a=0, b=1;

	for(i = 1; i < n; i ++){
		a += b;
		b = a-b;
	}

	printf("%lu\n", a);
}
```
```c
#include <stdio.h>

int fibonacci(int);

int main(){
	long i, result, n=20;

	for(i = 1; i < n; i ++){
		result = fibonacci(i);
	}

	printf("%lu\n", result);
	return 0;
}

int fibonacci(int n)
{
	if(n == 0 || n == 1)
		return n;
	else
		return fibonacci(n-1)+fibonacci(n-2);
}
```
> uftrace script
> uftrace record fibo_
> uftrace replay
> uftrace record --auto-args fibo_
> uftrace record -S script/count.py --auto-args fibo_ // 함수가 호출 반환되는 시점을 돌입하는 지점에서 파이썬 스크립트에 이미 약속되어있는 펑션을 호출해줌


jeniffer soft apm(application performance montoring system)같이 웹 대시보드

수많은 프로그램 함수중에 특정 함수 구간은 잦은 호출이 일어남, 병목이 일어날 수도 있음, 
