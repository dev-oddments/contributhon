# 2018 OSS Contributhon | 8/16 ~ 10/31 - [[Link]](https://contributhon.kr)

> Study about OSS(Open Source Software)contribution | [uftrace](https://github.com/namhyung/uftrace)

## uftrace track
* mentor: 송태웅 / 박한범 / 김재중
* goal: (I haven't set it yet)

## Journey
- [개회식](opening-ceremony.md), [KOSSCON](kosscon-2018.md) - 8/16
- [Day 1](record_day1.md) - 8/20
- [Day 2](record_day2.md) - 8/27
- Day 3(9/10)

## Link
- contributhon [dashboard](https://github.com/kosslab-kr/kosscontributhon2018)
- uftrace [kosslab]
---

## folder structure
```
├── arch
|   ├── aarch64
|   |   ├── Makefile : 
|   |   ├── cpuinfo.c : 
|   |   ├── mcount-arch.h : 
|   |   ├── mcount-support.c : 
|   |   ├── mcount.S : 
|   |   ├── plthook.S : 
|   |   └── regs.c : 
|   ├── arm 
|   |   ├── Makefile : 
|   |   ├── cpuinfo.c : 
|   |   ├── mcount-arch.h : 
|   |   ├── mcount-support.c : 
|   |   ├── mcount.S : 
|   |   ├── plthook.S : 
|   |   └── regs.c : 
|   ├── i386
|   |   ├── Makefile : 
|   |   ├── cpuinfo.c : 
|   |   ├── fentry.S : 
|   |   ├── mcount-arch.h : 
|   |   ├── mcount-dynamic.c : 
|   |   ├── mcount-support.c : 
|   |   ├── mcount.S : 
|   |   ├── plthook.S : 
|   |   └── regs.c : 
|   └── x86_64
|       ├── Makefile : 
|       ├── cpuinfo.c : 
|       ├── fentry.S : 
|       ├── mcount-arch.h : 
|       ├── mcount-dynamic.c : 
|       ├── mcount-support.c : 
|       ├── mcount.S : 
|       ├── plthook.S : 
|       ├── regs.c : 
|       ├── symbol.c : 
|       └── xray.S : 
├── check-deps
|   ├── Makefile : 
|   ├── Makefile.check : 
|   ├── _arm_has_hardfp.c : 
|   ├── _cc_has_mfentry.c : 
|   ├── _cc_has_mno_sse2.c : 
|   ├── _cc_has_wstringop_truncation.c : 
|   ├── _clock_without_librt.c : 
|   ├── _cxa_demangle.c : 
|   ├── _have_libdw.c : 
|   ├── _have_libelf.c : 
|   ├── _have_libncurses.c : 
|   ├── _have_libpython2.7.c : 
|   ├── _perf_clockid.c : 
|   └── _perf_context_switch.c : 
├── cmds
|   ├── dump.c : 
|   ├── graph.c : 
|   ├── info.c : 
|   ├── live.c : 
|   ├── record.c : 
|   ├── recv.d : 
|   ├── replay.c : 
|   ├── report.c : 
|   ├── script.c : 
|   └── tui.c : 
├── doc 
|   ├── Makefile
|   ├── uftrace-dump.md
|   ├── uftrace-graph.md
|   ├── uftrace-info.md
|   ├── uftrace-live.md
|   ├── uftrace-record.md
|   ├── uftrace-recv.md
|   ├── uftrace-replay.md
|   ├── uftrace-report.md
|   ├── uftrace-script.md
|   ├── uftrace-tui.md
|   └── uftrace.md
├── gdb/uftrace 
|   ├── lists.py
|   ├── mcount.py
|   ├── plthook.py
|   ├── rbtree.py
|   ├── trigger.py
|   └── utils.py
├── libmcount
|   ├── dynamic.c
|   ├── event.c
|   ├── internal.h
|   ├── mcount-nop.c
|   ├── mocunt.c
|   ├── mocunt.h
|   ├── misc.c
|   ├── plthook.c
|   ├── pmu.c
|   ├── record.c
|   └── wrap.c
├── libtraceevent
|   ├── include
|   |   ├── asm
|   |   |   └── bug.h
|   |   └── linux
|   |       └── compiler.h
|   ├── Makefile
|   ├── event-parse.c
|   ├── event-parse.h
|   ├── event-plugin.c
|   ├── event-utils.h
|   ├── kbuffer-parse.c
|   ├── kbuffer.h
|   ├── parse-filter.c
|   ├── parse-utils.c
|   └── trace-seq.c
├── misc
|   ├── apply-patch.sh
|   ├── bash-completion.sh
|   ├── debug-mcount.cmd
|   ├── debug.sh
|   ├── demangler.c
|   ├── gen-autoargs.py
|   ├── install-elfutils.sh
|   ├── prototypes.h
|   ├── run-lcov.sh
|   ├── symbols.c
|   ├── ubuntu-install-deps.sh
|   └── version.sh
├── scripts
|   ├── count.py
|   ├── info.py
|   ├── replay.py
|   ├── report-libcall.py
|   ├── simple.py
|   └── trace-memcpy.py
├── tests/
├── utils
|   ├── asm.h
|   ├── auto-args.c
|   ├── auto-args.h
|   ├── compiler.h
|   ├── data-file.c
|   ├── debug.c
|   ├── demangle.c
|   ├── dwarf.c
|   ├── dwarf.h
|   ├── field.c
|   ├── field.h
|   ├── filter.c
|   ├── filter.h
|   ├── fstack.c
|   ├── fstack.h
|   ├── graph.c
|   ├── graph.h
|   ├── kernel.c
|   ├── kernel.h
|   ├── list.h
|   ├── pager.c
|   ├── perf.c
|   ├── perf.h
|   ├── rbtree.c
|   ├── rbtree.h
|   ├── script-python.c
|   ├── script-python.h
|   ├── script.c
|   ├── script.h
|   ├── session.c
|   ├── symbol-libelf.c
|   ├── symbol-rawelf.c
|   ├── symbol-rawelf.h
|   ├── symbol.c
|   ├── symbol.h
|   ├── utils.c
|   └── utils.h
├── .travis.yml
├── Makefile
├── Makefile.include
├── configure
├── uftrace-gdb.py
├── uftrace.c
└── uftrace.h
```

---

## contribute other project
- [first-contributions](https://github.com/Roshanjossey/first-contributions)
- [your-first-PR](https://github.com/yourfirstpr/yourfirstpr.github.io)
- [awesome](https://github.com/sindresorhus/awesome)


## Classify opensource lisence
### 1. GNU GPL(General Public License)
> GPL [FAQ](https://www.gnu.org/licenses/gpl-faq.en.html)
* 유료로 판매 가능하지만 전체소스를 공개해야 함 
* 내부적인 목적으로만 사용할 때 소스코드를 공개 할 필요 없지만 외부에 배포할 때에는 전체소스를 공개해야 함 
* GPL 코드를 일부라도 사용하게되면 전체를 배포할 때에는 GPL을 적용해야 함

### 2. GNU LGPL(Lesser General Public license)
* LGPL코드를 정적 혹은 동적 라이브러리로 사용한 프로그램을 개발하여 판매/배포할 경우에 소스코드를 공개하지 않아도 됨

### 3. BSD(Berkeley Software Distribution) License
* 아무런 제한이 없음 - 소스코드 공개 의무가 없으며 상용 소프트웨어에서도 사용 가능 

### 4. MIT License
* copyright와 license에 대한 정보만 표기하면 자유롭게 사

## Issue tip
```
ENH: 새기능 혹은 개선
BUG: 버그수정
DOC: 문서 업데이트
TST: 테스트 업데이트
BLD: 빌드 관련 업데이트
PERF: 성능개선
CLN: 코드정리

feat: 새로운 기능을 추가할 경우
fix: 버그를 고친 경우
docs: 문서 수정한 경우
style: 코드 포맷 변경, 세미 콜론 누락, 코드 수정이 없는 경우
refactor: 프로덕션 코드 리팩터링
test: 테스트 추가, 테스트 리팩터링 (프로덕션 코드 변경 없음)
chore: 빌드 테스크 업데이트, 패키지 매니저 설정할 경우 (프로덕션 코드 변경 없음)
[출처](https://sujinlee.me/professional-github/)
```

## My thought
어떤것에 기여한다는건 코드에만 해당하는 사항이 아니다. 이를테면 블로그라던지 혹은 번역활동 등을 통해 그것에 공헌할 수 있을것이다. 너무 거창하게 생각하지말고 작은것부터 천천히 노력해나가면 될 것 같다. 다만 꾸준히 하는게 가장 중요한 요소라고 할 수 있을 것이다.

## 목록 
- 번역 :

## 참고할 것 
- [naver open source guide](https://naver.github.io/OpenSourceGuide/book/)
- [codetriage](https://www.codetriage.com/)
- [open source guide](https://opensource.guide/legal/)
- [first-timers-only](https://www.firsttimersonly.com)
- [oepn source firday]()
- [up-for-grabs](https://up-for-grabs.net/#/)
- [contributor-ninja](https://contributor.ninja)
- [24 pull requests](https://24pullrequests.com/)

- [github opensource guide](https://opensource.guide/how-to-contribute/#finding-a-project-to-contribute-to)
https://www.openhub.net/

## Documentation
- LaTeX - [Awesome CI](https://github.com/posquit0/Awesome-CV)
- perfbook - [Korean-translate](https://github.com/sjp38/perfbook-ko_KR)
- README.md - [badge](https://github.com/Naereen/badges)
