# uftrace
## uftrace 내부 구조(internals)와 소스코드에 대한 설명
> 이해하려고 하면 어렵다 그낭 받아들이자!
summit 발표자료 appendix부분

* -pg option
  * mcount를 호출하는 부분을 추가하게 됨 
  * 함수호출 흐름이 uftrace로 들어오게 됨

* gdb
  * disas main
    > disassemble main function 
  * list
  * quit
  * b *main+8
  * c
  * si
  * x/gx $rsp
  * r
  * info proc mapping

* got table
  * 프로세서가 가지고 있는 메모리의 이정표
  * 오프셋 절대값을 바인딩

* plt -> got -> linking // 이 매커니즘에 기반해서 함수가 호출되는 시점과 종료되는 시점에 대한 
  * plt는 명령어 3개로 이루어져 있음
    1. got를 이용해 plt 2번째 주소로 점프
    2. 시스템에서 linking해주는 함수로 들어가야 함
    3. linking을 해주는 애는 plt hooker고.. 그래서 utftracing이 가능함. 
* rage binding

함수호출 흐름이 uftrace로 들어오게 됨 
