# Contributhon
## Index
1. [2019 Open Software Training](#2019ost)
1. [2019 OSS Contributhon - React Native Tutorial](#2019)
2. [2018 OSS Contributhon - Uftrace](#2018)

# 2019 Open Software Training | 2019 Fall Semester <a name="2019ost"></a>
## 1. 일정
- [ ] 11/01 : 중간발표
- [ ] 12/13 : 최종발표
- [ ] 12/20 : 멘토링

## 2. ToDo
- [ ] Make [Hyper](https://github.com/zeit/hyper) extension 
- [ ] Contribute [RNRF](https://github.com/aksonov/react-native-router-flux)
- [ ] Create Open Source RN module
- [ ] Make Electron prj
- ...


# 2019 OSS Contributhon | 2019 09/07 ~ 10/20 <a name="2019"></a>
> Study about OSS(Open Source Software)contribution | [react-native-tutorial](https://github.com/JeffGuKang/react-native-tutorial)

## react-native-tutorial 
- Mentor: 강명구
- Goal: React Native 튜토리얼 제작

## 1. 일정
- [x] 9/21 : 오프라인 멘토링
- [x] 9/29(일) : 중간보고
  - [x] [2019-Contributhon-중간보고서-이용재](react-native-tutorial/2019-Contributhon-중간보고서-이용재.pdf)
- [x] 10/12(토) : 오프라인 멘토링
- [x] 10/20(일) : 결과보고
  - [x] [2019-Contributhon-결과보고서-이용재](react-native-tutorial/2019-Contributhon-결과보고서-이용재.pdf)
- [ ] 11/2(토) : 발표심사

## 2. Guideline
- 폴더구조
  - 코드:
    - 한개인 경우 - `Examples/BasicTutorial/`
    - 여러개인 경우
      - `Examples/StateManagement/SetState`
      - `Examples/StateManagement/MobX`
      - `Examples/StateManagement/Redux`
  - 문서:
    - `docs/state-tutorial/set-state-basic-tutorial/01-getting-started/getting-started.md`
    - `docs/state-tutorial/redux-tutorial/01-getting-started/getting-started.md`
    - `docs/state-tutorial/mobx-tutorial/01-getting-started/getting-started.md`
- 진행과정(gitflow 방식 사용)
  - 구현할 부분(작성할 부분)에 대해서 Issue 작성
  - 최신사항 반영 - `git fetch upstream`
  - upstream/state-tutorial 브랜치에서 작업 브랜치(upstream/state-tutorial/{issueNum}-setState-tutorial)를 생성
    - `git checkout -b {issueNum}-state-tutorial --track upstream/basic-tutorial`
  - 소스코드 수정
  - 변경사항 커밋: `git commit -m 'Add a setState tutorial in state-tutorial #{issueNum}`
  - 변경사항 커밋: `git commit -m 'Add a setState tutorial example project #{issueNum}`
  - 최신사항 반영 Rebase: `git pull --rebase upstream state-tutorial`
  - 본인 Fork 레파지토리인 Origin에 Push: `git push origin`
  - 본인 origin Github에서 {issueNum}-state-tutorial 브랜치를 upstream/state-tutorial 에 PR을 생성
  - 1명 이상의 팀원이 리뷰 후 승인 (approve)
  - 팀장이 Merge
- PR Template
  - `Fix`
    - 왜 이 PR이 요구되는지, 코드 변화가 필요한 이유가 무엇인지 (여기서 #다음에 이슈번호를 적으면 해당 이슈와 연결됩니다, 추후 확인시에 유용해요)
  - `Changes`
    - 위의 요구사항에 따라 실제로 어떤 변경을 했는지
  - `How Verified`
    - 바뀐 변경사항을 어떻게 테스트하였는지 (Automated - 자동[린트와 같은 것들], Manually - 수동[직접 실행해서 테스트한 것들])
  - `Notes`
    - 추후 작업 시 알아두어야 할 것들 (버그나 에러 가능성에 대한 언급, 잔여 작업에 대한 설명 등)
  - `References`
    - 참고한 사이트나 자료들

## 3. tip
- `git log` 커스터마이즈
  - [https://coderwall.com/p/euwpig/a-better-git-log](https://coderwall.com/p/euwpig/a-better-git-log)
  - 현재 브랜치의 log만 보기: `git lg`
    - `git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"`
  - 모든 브랜치의 log 보기: `git lga`
    - `git config --global alias.lga "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --all"`
- `git add .` 대체
  - [https://blog.outsider.ne.kr/1247](https://blog.outsider.ne.kr/1247)
  - `git add .`는 절대로 쓰면 안됨
    - 어떤 내용을 커밋에 포함되는지가 완전히 감춰짐
  - `git add -p`
    - 스테이징 하는 변경사항 확인 가능하므로 실수를 방지할 수 있음
  - `git commit -v`
    - 커밋하기 전 변경사항을 확인할 수 있으므로 실수를 방지할 수 있음
- track 기준으로부터 branch가 생성되도록
  - `git checkout -b aaa --track upstream/tutorial/router`


# 2018 OSS Contributhon | 2018 08/16 ~ 10/31 <a name="2018"></a>
> Study about OSS(Open Source Software)contribution | [uftrace](https://github.com/namhyung/uftrace)

## uftrace track
- mentor: 송태웅 / 박한범 / 김재중
- goal: patch uftrace version(0.8.3 to 0.9)on yocto(http://layers.openembedded.org/layerindex/recipe/68075/)

## Journey
- [개회식](opening-ceremony.md), [KOSSCON](kosscon-2018.md) - 8/16
- [Day 1](record_day1.md) - 8/20
- [Day 2](record_day2.md) - 8/27
- [Day 3](record_day3.md) - 9/10
- [Day 4](record_day4.md) - 9/17
- [Day 6](record_day6.md) - 10/15

## Link
- contributhon [dashboard](https://github.com/kosslab-kr/kosscontributhon2018)
- uftrace [kosslab](https://github.com/kosslab-kr/uftrace)
- [2016](https://2016.kosshackathon.kr/#kosshack_prize)
- [2017](https://2017.contributhon.kr/)
- [linux-perf](https://github.com/kosslab-kr/linux-perf/issues)

---

## folder structure
> tree 명령어를 사용하면 간단하게 폴더구조를 출력할 수 있다.

```
.
├── 1
├── 1.md
├── CONTRIBUTING.md
├── COPYING
├── INSTALL.md
├── Makefile
├── Makefile.include
├── NEWS
├── README.md
├── TODO
├── arch
│   ├── aarch64
│   │   ├── Makefile
│   │   ├── cpuinfo.c
│   │   ├── mcount-arch.h
│   │   ├── mcount-support.c
│   │   ├── mcount.S
│   │   ├── plthook.S
│   │   └── regs.c
│   ├── arm
│   │   ├── Makefile
│   │   ├── cpuinfo.c
│   │   ├── mcount-arch.h
│   │   ├── mcount-support.c
│   │   ├── mcount.S
│   │   ├── plthook.S
│   │   └── regs.c
│   ├── i386
│   │   ├── Makefile
│   │   ├── common.S
│   │   ├── cpuinfo.c
│   │   ├── fentry.S
│   │   ├── mcount-arch.h
│   │   ├── mcount-dynamic.c
│   │   ├── mcount-support.c
│   │   ├── mcount.S
│   │   ├── plthook.S
│   │   └── regs.c
│   └── x86_64
│       ├── Makefile
│       ├── cpuinfo.c
│       ├── fentry.S
│       ├── mcount-arch.h
│       ├── mcount-dynamic.c
│       ├── mcount-event.c
│       ├── mcount-support.c
│       ├── mcount.S
│       ├── plthook.S
│       ├── regs.c
│       ├── symbol.c
│       └── xray.S
├── check-deps
│   ├── Makefile
│   ├── Makefile.check
│   ├── __arm_has_hardfp.c
│   ├── __cc_has_mfentry.c
│   ├── __cc_has_mno_sse2.c
│   ├── __cc_has_wstringop_truncation.c
│   ├── __clock_without_librt.c
│   ├── __cxa_demangle.c
│   ├── __have_libdw.c
│   ├── __have_libelf.c
│   ├── __have_libncurses.c
│   ├── __have_libpython2.7.c
│   ├── __perf_clockid.c
│   └── __perf_context_switch.c
├── cmds
│   ├── dump.c
│   ├── graph.c
│   ├── info.c
│   ├── live.c
│   ├── record.c
│   ├── recv.c
│   ├── replay.c
│   ├── report.c
│   ├── script.c
│   └── tui.c
├── configure
├── doc
│   ├── Makefile
│   ├── uftrace-chrome.png
│   ├── uftrace-dump.md
│   ├── uftrace-graph.md
│   ├── uftrace-info.md
│   ├── uftrace-live-demo.gif
│   ├── uftrace-live.md
│   ├── uftrace-record.md
│   ├── uftrace-recv.md
│   ├── uftrace-replay.md
│   ├── uftrace-report.md
│   ├── uftrace-script.md
│   ├── uftrace-tui.md
│   └── uftrace.md
├── gdb
│   └── uftrace
│       ├── lists.py
│       ├── mcount.py
│       ├── plthook.py
│       ├── rbtree.py
│       ├── trigger.py
│       └── utils.py
├── libmcount
│   ├── dynamic.c
│   ├── event.c
│   ├── internal.h
│   ├── mcount-nop.c
│   ├── mcount.c
│   ├── mcount.h
│   ├── misc.c
│   ├── plthook.c
│   ├── pmu.c
│   ├── record.c
│   └── wrap.c
├── libtraceevent
│   ├── Makefile
│   ├── event-parse.c
│   ├── event-parse.h
│   ├── event-plugin.c
│   ├── event-utils.h
│   ├── include
│   │   ├── asm
│   │   │   └── bug.h
│   │   └── linux
│   │       └── compiler.h
│   ├── kbuffer-parse.c
│   ├── kbuffer.h
│   ├── parse-filter.c
│   ├── parse-utils.c
│   └── trace-seq.c
├── misc
│   ├── apply-patch.sh
│   ├── bash-completion.sh
│   ├── debug-mcount.cmd
│   ├── debug.sh
│   ├── demangler.c
│   ├── gen-autoargs.py
│   ├── install-elfutils.sh
│   ├── prototypes.h
│   ├── run-lcov.sh
│   ├── symbols.c
│   ├── ubuntu-install-deps.sh
│   └── version.sh
├── scripts
│   ├── count.py
│   ├── info.py
│   ├── replay.py
│   ├── report-libcall.py
│   ├── simple.py
│   └── trace-memcpy.py
├── tests
│   ├── Makefile
│   ├── arch
│   │   ├── arm
│   │   │   ├── Makefile
│   │   │   ├── a.c
│   │   │   ├── t.c
│   │   │   └── thumb.c
│   │   └── x86_64
│   │       ├── Makefile
│   │       └── fentry.c
│   ├── runtest.py
│   ├── s-abc.c
│   ├── s-alloca.c
│   ├── s-allocfree.c
│   ├── s-arg.c
│   ├── s-autoargs.c
│   ├── s-backtrace.cpp
│   ├── s-daemon.c
│   ├── s-demangle.cpp
│   ├── s-diff.c
│   ├── s-dlopen.c
│   ├── s-dlopen2.cpp
│   ├── s-dwarf1.c
│   ├── s-dwarf2.cpp
│   ├── s-dwarf3.cpp
│   ├── s-enum.c
│   ├── s-exception.cpp
│   ├── s-exception2.cpp
│   ├── s-exception3.cpp
│   ├── s-exception4.cpp
│   ├── s-exit.c
│   ├── s-exp-char.c
│   ├── s-exp-float.c
│   ├── s-exp-int.c
│   ├── s-exp-mixed.c
│   ├── s-exp-str.c
│   ├── s-fibonacci.c
│   ├── s-float-libcall.c
│   ├── s-fork.c
│   ├── s-fork2.c
│   ├── s-forkexec.c
│   ├── s-getids.c
│   ├── s-hello.c
│   ├── s-lib.c
│   ├── s-libbar.cpp
│   ├── s-libbaz.cpp
│   ├── s-libfoo.cpp
│   ├── s-libmain.c
│   ├── s-longjmp.c
│   ├── s-longjmp2.c
│   ├── s-longjmp3.c
│   ├── s-malloc-fork.c
│   ├── s-malloc-hook.c
│   ├── s-malloc-tsd.c
│   ├── s-malloc.c
│   ├── s-mmap.c
│   ├── s-namespace.cpp
│   ├── s-nest-libcall.c
│   ├── s-nested.c
│   ├── s-openclose.c
│   ├── s-pltarg.c
│   ├── s-posix_spawn.c
│   ├── s-racycount.c
│   ├── s-return.c
│   ├── s-sdt.c
│   ├── s-signal.c
│   ├── s-signal2.c
│   ├── s-sleep.c
│   ├── s-sort.c
│   ├── s-std-string.cpp
│   ├── s-taskname.c
│   ├── s-thread-exec.c
│   ├── s-thread-exit.c
│   ├── s-thread-name.c
│   ├── s-thread-tsd.c
│   ├── s-thread.c
│   ├── s-ucontext.c
│   ├── s-variadic.c
│   ├── s-vforkexec.c
│   ├── t001_basic.py
│   ├── t002_argument.py
│   ├── t003_thread.py
│   ├── t004_filter_F.py
│   ├── t005_filter_N.py
│   ├── t006_filter_FN.py
│   ├── t007_library.py
│   ├── t008_daemon.py
│   ├── t009_fork.py
│   ├── t010_forkexec.py
│   ├── t011_vforkexec.py
│   ├── t012_demangle.py
│   ├── t013_signal.py
│   ├── t014_ucontext.py
│   ├── t015_longjmp.py
│   ├── t016_alloca.py
│   ├── t017_no_libcall.py
│   ├── t018_filter_regex.py
│   ├── t019_full_depth.py
│   ├── t020_filter_depth.py
│   ├── t021_filter_plt.py
│   ├── t022_filter_kernel.py
│   ├── t023_replay_filter.py
│   ├── t024_report_basic.py
│   ├── t025_report_s_call.py
│   ├── t026_filter_trigger.py
│   ├── t027_replay_filter_d.py
│   ├── t028_replay_backtrace.py
│   ├── t029_trigger_only.py
│   ├── t030_replay_trigger.py
│   ├── t031_filter_demangle1.py
│   ├── t032_filter_demangle2.py
│   ├── t033_filter_demangle3.py
│   ├── t034_filter_demangle4.py
│   ├── t035_filter_demangle5.py
│   ├── t036_replay_filter_N.py
│   ├── t037_trace_onoff.py
│   ├── t038_trace_disable.py
│   ├── t039_trace_onoff_F.py
│   ├── t040_replay_onoff.py
│   ├── t041_replay_onoff_N.py
│   ├── t042_live_disable.py
│   ├── t043_full_demangle.py
│   ├── t044_report_avg_total.py
│   ├── t045_report_avg_self.py
│   ├── t046_report_threads.py
│   ├── t047_signal2.py
│   ├── t048_malloc_impl.py
│   ├── t049_column_view.py
│   ├── t050_no_pltbind.py
│   ├── t051_return.py
│   ├── t052_nested_func.py
│   ├── t053_filter_time.py
│   ├── t054_filter_time_F.py
│   ├── t055_filter_time_N.py
│   ├── t056_filter_time_T.py
│   ├── t057_filter_time_D.py
│   ├── t058_arg_int.py
│   ├── t059_arg_str.py
│   ├── t060_arg_fmt.py
│   ├── t061_arg_plt.py
│   ├── t062_arg_char.py
│   ├── t063_retval.py
│   ├── t064_trigger_trace.py
│   ├── t065_arg_order.py
│   ├── t066_no_demangle.py
│   ├── t067_report_diff.py
│   ├── t068_filter_time_A.py
│   ├── t069_graph.py
│   ├── t070_graph_backtrace.py
│   ├── t071_graph_depth.py
│   ├── t072_no_comment.py
│   ├── t073_lib_filter.py
│   ├── t074_lib_trigger.py
│   ├── t075_lib_arg.py
│   ├── t076_lib_replay_F.py
│   ├── t077_lib_replay_T.py
│   ├── t078_max_stack.py
│   ├── t079_replay_kernel_D.py
│   ├── t080_replay_kernel_D2.py
│   ├── t081_kernel_depth.py
│   ├── t082_arg_many.py
│   ├── t083_arg_float.py
│   ├── t084_arg_mixed.py
│   ├── t085_arg_reg.py
│   ├── t086_arg_stack.py
│   ├── t087_arg_variadic.py
│   ├── t088_graph_session.py
│   ├── t089_graph_exit.py
│   ├── t090_report_recursive.py
│   ├── t091_replay_tid.py
│   ├── t092_report_tid.py
│   ├── t093_report_filter.py
│   ├── t094_report_depth.py
│   ├── t095_graph_tid.py
│   ├── t096_graph_filter.py
│   ├── t097_dump_basic.py
│   ├── t098_dump_tid.py
│   ├── t099_dump_filter.py
│   ├── t100_dump_depth.py
│   ├── t101_dump_chrome.py
│   ├── t102_dump_flamegraph.py
│   ├── t103_dump_kernel.py
│   ├── t104_graph_kernel.py
│   ├── t105_replay_time.py
│   ├── t106_report_time.py
│   ├── t107_dump_time.py
│   ├── t108_graph_time.py
│   ├── t109_replay_time_A.py
│   ├── t110_replay_time_T.py
│   ├── t111_kernel_tid.py
│   ├── t112_replay_skip.py
│   ├── t113_trigger_time.py
│   ├── t114_replay_trg_time.py
│   ├── t115_replay_field.py
│   ├── t116_field_none.py
│   ├── t117_time_range.py
│   ├── t118_thread_tsd.py
│   ├── t119_malloc_hook.py
│   ├── t120_malloc_tsd.py
│   ├── t121_malloc_fork.py
│   ├── t122_time_range2.py
│   ├── t123_backtrace.py
│   ├── t124_exception.py
│   ├── t125_report_range.py
│   ├── t126_arg_regex.py
│   ├── t127_arg_module.py
│   ├── t128_arg_module2.py
│   ├── t129_session_tid.py
│   ├── t130_thread_exec.py
│   ├── t131_lib_dlopen.py
│   ├── t132_trigger_kernel.py
│   ├── t133_long_string.py
│   ├── t134_pic_pie.py
│   ├── t135_trigger_time2.py
│   ├── t136_dynamic.py
│   ├── t137_kernel_tid_update.py
│   ├── t138_kernel_dynamic.py
│   ├── t139_kernel_dynamic2.py
│   ├── t140_dynamic_xray.py
│   ├── t141_recv_basic.py
│   ├── t142_recv_multi.py
│   ├── t143_recv_kernel.py
│   ├── t144_longjmp2.py
│   ├── t145_longjmp3.py
│   ├── t146_arg_std_string.py
│   ├── t147_event_sdt.py
│   ├── t148_event_kernel.py
│   ├── t149_event_kernel2.py
│   ├── t150_recv_event.py
│   ├── t151_recv_runcmd.py
│   ├── t152_read_proc_statm.py
│   ├── t153_read_page_fault.py
│   ├── t154_keep_pid.py
│   ├── t155_trigger_finish.py
│   ├── t156_trigger_finish2.py
│   ├── t157_script_python.py
│   ├── t158_report_diff_policy1.py
│   ├── t159_report_diff_policy2.py
│   ├── t160_report_diff_policy3.py
│   ├── t161_pltbind_now.py
│   ├── t162_pltbind_now_pie.py
│   ├── t163_event_sched.py
│   ├── t164_report_sched.py
│   ├── t165_graph_sched.py
│   ├── t166_dump_sched.py
│   ├── t167_recv_sched.py
│   ├── t168_lib_nested.py
│   ├── t169_script_args.py
│   ├── t170_script_filter.py
│   ├── t171_script_option.py
│   ├── t172_trigger_filter.py
│   ├── t173_trigger_args.py
│   ├── t174_replay_filter_kernel.py
│   ├── t175_filter_time_read.py
│   ├── t176_arg_fptr.py
│   ├── t177_report_diff_policy4.py
│   ├── t178_arg_auto1.py
│   ├── t179_arg_auto2.py
│   ├── t180_arg_auto3.py
│   ├── t181_graph_full.py
│   ├── t182_thread_exit.py
│   ├── t183_info_quote.py
│   ├── t184_arg_enum.py
│   ├── t185_exception2.py
│   ├── t186_exception3.py
│   ├── t187_graph_field.py
│   ├── t188_graph_field_none.py
│   ├── t189_replay_field2.py
│   ├── t190_trigger_autoargs.py
│   ├── t191_posix_spawn.py
│   ├── t192_lib_name.py
│   ├── t193_read_pmu_cycle.py
│   ├── t194_read_pmu_cache.py
│   ├── t195_read_pmu_branch.py
│   ├── t196_chrome_taskname.py
│   ├── t197_filter_glob.py
│   ├── t198_lib_arg_float.py
│   ├── t199_script_info.py
│   ├── t200_lib_dlopen2.py
│   ├── t201_arg_dwarf1.py
│   ├── t202_arg_dwarf2.py
│   ├── t203_arg_dwarf3.py
│   ├── t204_arg_dwarf4.py
│   ├── t205_arg_auto4.py
│   ├── t206_arg_enum2.py
│   ├── unittest.c
│   └── unittest.h
├── uftrace-gdb.py
├── uftrace.c
├── uftrace.h
└── utils
    ├── asm.h
    ├── auto-args.c
    ├── auto-args.h
    ├── compiler.h
    ├── data-file.c
    ├── debug.c
    ├── demangle.c
    ├── dwarf.c
    ├── dwarf.h
    ├── field.c
    ├── field.h
    ├── filter.c
    ├── filter.h
    ├── fstack.c
    ├── fstack.h
    ├── graph.c
    ├── graph.h
    ├── kernel.c
    ├── kernel.h
    ├── list.h
    ├── pager.c
    ├── perf.c
    ├── perf.h
    ├── rbtree.c
    ├── rbtree.h
    ├── script-python.c
    ├── script-python.h
    ├── script.c
    ├── script.h
    ├── session.c
    ├── symbol-libelf.c
    ├── symbol-libelf.h
    ├── symbol-rawelf.c
    ├── symbol-rawelf.h
    ├── symbol.c
    ├── symbol.h
    ├── utils.c
    └── utils.h
```

- arch/ :
- check-deps/ :
- cmds/ :
- docs/ :
- gdb/ :
- libmcount/ :
- libraceevnet/ :
- mis/ :
- script/ :
- tests/ :
- utils/ :

---

## contribute other project
- [first-contributions](https://github.com/Roshanjossey/first-contributions)
- [your-first-PR](https://github.com/yourfirstpr/yourfirstpr.github.io)
- [awesome](https://github.com/sindresorhus/awesome)

## Classify opensource lisence

### 1. GNU GPL(General Public License)
> GPL [FAQ](https://www.gnu.org/licenses/gpl-faq.en.html)

- 유료로 판매 가능하지만 전체소스를 공개해야 함
- 내부적인 목적으로만 사용할 때 소스코드를 공개 할 필요 없지만 외부에 배포할 때에는 전체소스를 공개해야 함
- GPL 코드를 일부라도 사용하게되면 전체를 배포할 때에는 GPL을 적용해야 함

### 2. GNU LGPL(Lesser General Public license)
- LGPL코드를 정적 혹은 동적 라이브러리로 사용한 프로그램을 개발하여 판매/배포할 경우에 소스코드를 공개하지 않아도 됨

### 3. BSD(Berkeley Software Distribution) License
- 아무런 제한이 없음 - 소스코드 공개 의무가 없으며 상용 소프트웨어에서도 사용 가능

### 4. MIT License
- copyright와 license에 대한 정보만 표기하면 자유롭게 사

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
