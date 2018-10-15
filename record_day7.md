# day #

## pg옵션 없이 컴파일해서 ..

## todo 파일 내용들에 대한 것 - maintainer 남형님
- 유저프로그램(c or c++)에 관해서 트레이싱 하는 것
- python에 관련해서도 현재 구상중

### Cleanup task management
task정보가지 2가지 구조체에 정리되어 있음
- struct uftrace_task
- struct ftrace_task_funciton

### More trigger actions
- Read
- Watch : 최근 cpu 정보 추가
- Counting
- Ignoring

### Improve documentation
- Honggyu Added slide at
 + 
- We have wiki as well
 + https://github.com/namhyung/uftrace/wiki

### Report with multi-thread
- Big data takes a time to process
- Uftrace data has data files for each task, cpu
- Replay needs record sorted by time
- But report, graph don't

### Value filter
- Filter by value of function argumetns/return
 + Filtering at runtime
  
### Size filter
- Filter by (byte) size of function

### Location filter : file path르 보고 tracing
- Filter by source location of function
  - Filtering at load-time
  - Need DWARF debug info
    + handle relative path

### Caller filter : 현재 구현은 함 // malloc을 불리는 경로만 남기고 나머진 없앰 / 함수가 불리는 path르 찾아줌
- Filtering at runtime
- Done(#166)

### SDT argument support : 자기가 원하는 소스 위치에다가 
- currently only provier/event name is recorded
- SDTv3 allows arguments
- But it needs to parse its format
- Which is cpu-specific

### LTT-ng evnet support : Linux Tracing Tool
### Symbol file compression : symbol 파일을 text로 저장하는걸 교체
### Watch point
- -W cpu was added
- But global variable is not yet supported
  + Symbol for variable
  + Concurrency should be considered
  
### Kernel function argument
- Adding kprobe
  - parse argument info from the kprobe
  - Apply it to the normal function record
  - Consider preemption by interupts

### Different clock support : 보정해야함
- clock_gettime(MONORONIX)
  - can be slow
  - VDSP is still slow
- X86 has TSC
  - Not changed by cpufreq
  - Needs to sync with monotonic clock

### Report field
- Report has fixed fields
  - Total time, self time, call
  - Avg total, min total, max total
  - Avg self, min self, max self
- Make it selectable any fields (like replay -f)
- Sort should be supported too

### TUI update
- Filter change
- Field change
- Sort support (for report)
- open/close data
- Replay (with folding) * 유일하게 안됨

### Python update
- Python3 support
  - Maintain both 2 and 3 compatibility
- Python function tracing (#436)
  - C extension for sys.settrace()
  - Function entry/exit
  - Calls libmcount functions internally

### Script update
- Improve python scripts
  - Memory alloc/free stat
  - File open/close stat
- Writing new scripts
  - Spinlock/Mutex lock/unlock stat?
- Other lnaguage support
- And so on...

### Attach to process // pipe룰 쓰되 naming pipe를 만들든지 하는 새로운 통신 방식을 만들어야 함, arument 정보 넘기는 것, tracing 정보 받느 것
- Attach by ptrace
- Injext libmcount (or similar)
- Run initialization by single thread
  - Communicate by named-pipe or unix socket?
- Probably need dynamic tracing
- detach and trace
- Restore original state after tracing

### Dynamic tracing : 내가 원하는 것만 tracing 할 수 있도록
1. W/ compiler support (as of now)
2. Script to make mcount to NOP
3. Reverse patch making NOP runtime
4. Inject mcount call at load-time
5. Inject mcount call at runtime (w/ attach)

### Signal trigger 
- For daemon process (#340)
  + It doesn't exit
  - uftrace gathers info after the exit
  - Add 'finish' action
  - 'enable'/'disable' can be more efficient
    - Change first insn of mcount.S to 'ret'
    - How to restore original insn?
    
### Multi-date processing
- want to trace more than one process
  - Record separatly (at the same time)
  - Display togeether
  - Color 

### Graph diff support
- uftrace graph
  - Hilight different between two date
  - Good to know where's the problem
  - In TUI?

### Full demangle support : demangle - c++ // 현재는 외부 라이브러리로 구현
- Without external libarary
  - DWARF sometimes use full-demangled name
  - Hard to match with simple demangler
  - Finer control to demangler behavior
  
### Flat trace
- Trace function entry only
  - No need to hook return address - much safer!
  - Reduce overhead by 50%
  - Argument still supported
  - Guess depth from parent location (optional)
  - Kernal function tracer compatible

> rust 나 go(gcc-go) 같은것 / tracing 되어있는 것 // 어찌되었든 dynamic tracing이 되어야 함.

> osx and linux file format is not similar. // calling convention pfd

