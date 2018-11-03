## 주의할 점
- 빌드를 위해 50gb 이상 용량 확보하기
## 0.8.3에서의 에러 해결 과정
- build가 안되는 문제(i386에서 error)를 해결하기 위해 uftrace_0.8.3.bb파일 내부에 아래의 코드를 삽입해야 함
```
def set_target_arch(d):
     import re
     arch = d.getVar('TARGET_ARCH', True)
     if re.match(r'i.86', arch, re.I):
         return 'i386'
     else:
         return arch
 
 EXTRA_UFTRACE_OECONF = "ARCH=${@set_target_arch(d)} \
                         with_elfutils=/use/libelf/from/sysroot"
 
 do_configure() {
     ${S}/configure ${EXTRA_UFTRACE_OECONF}
 }
 
 FILES_SOLIBSDEV = ""
 FILES_${PN} += "${libdir}/*.so"
 
 COMPATIBLE_HOST = "(i.86|x86_64|aarch64|arm)"
 ```
 - 이후 이를 포함한 패치 전송 #xx
 
 ## 0.9버전으로 빌드하는 과정
 ```
 # v0.8.3
SRCREV = "8b723a6fae2ef30495cd6279774fba9c95cd9c88"
SRC_URI = "git://github.com/namhyung/${BPN} \
           file://0001-include-dlfcn.h-for-RTLD_DEFAULT.patch \
```
- SRCREV = "f0fed0b24a9727ffed04673b62f66baad21a1f99" 으로 교체 // 0.9버전 릴리즈에 해당하는 커밋id
- 0.9 버전에선 패치가 이미 적용되었으므로 SRC_URI 라인에서 해당 패치를 포함시키는 라인 삭제
- 0.9 버전에 적용해야 할 패치내용을 삽입 
   - file://0001-mcount-Use-renamed-struct-mcount_dynamic_info-fields.patch
- 이후 빌드 및 테스트
> bitbake uftrace -c cleanall; bitbake uftrace;

## bb
```bash
SUMMARY = "Trace and analyze execution of a program written in C/C++"
HOMEPAGE = "https://github.com/namhyung/uftrace"
BUGTRACKER = "https://github.com/namhyung/uftrace/issues"
SECTION = "devel"
LICENSE = "GPLv2"
LIC_FILES_CHKSUM = "file://COPYING;md5=b234ee4d69f5fce4486a80fdaf4a4263"
DEPENDS = "elfutils"
DEPENDS_append_libc-musl = " argp-standalone"
inherit autotools
# v0.8.3
SRCREV = "f0fed0b24a9727ffed04673b62f66baad21a1f99"
SRC_URI = "git://github.com/namhyung/${BPN}"
S = "${WORKDIR}/git"
LDFLAGS_append_libc-musl = " -largp"
def set_target_arch(d):
     import re
     arch = d.getVar('TARGET_ARCH', True)
     if re.match(r'i.86', arch, re.I):
         return 'i386'
     else:
         return arch
EXTRA_UFTRACE_OECONF = "ARCH=${@set_target_arch(d)} \
                        with_elfutils=/use/libelf/from/sysroot"
do_configure() {
    ${S}/configure ${EXTRA_UFTRACE_OECONF}
}
FILES_SOLIBSDEV = ""
FILES_${PN} += "${libdir}/*.so"
COMPATIBLE_HOST = "(i.86|x86_64|aarch64|arm)"
# uftrace supports armv6 and above
COMPATIBLE_HOST_armv4 = 'null'
COMPATIBLE_HOST_armv5 = 'null'
```
## log

```bash
Log data follows:
| DEBUG: SITE files ['endian-little', 'bit-32', 'ix86-common', 'common-linux', 'common-glibc', 'i586-linux', 'commo
n']
| DEBUG: Executing shell function do_compile
| NOTE: make -j 4
|   CC       cmds/recv.o
|   CC       cmds/script.o
|   CC       cmds/report.o
|   GEN      version.h
|   CC       cmds/tui.o
|   CC       cmds/replay.o
|   CC       cmds/dump.o
|   CC       cmds/live.o
|   CC       cmds/graph.o
|   CC       cmds/info.o
|   CC       cmds/record.o
|   CC       utils/symbol-rawelf.o
|   CC       utils/session.o
|   CC       utils/rbtree.o
|   CC       utils/perf.o
|   CC       utils/script.o
|   CC       utils/kernel.o
|   CC       utils/auto-args.o
|   CC       utils/data-file.o
|   CC       utils/dwarf.o
|   CC       utils/symbol-libelf.o
|   CC       utils/graph.o
|   CC       utils/field.o
|   CC       utils/demangle.o
|   CC       utils/filter.o
|   CC       utils/pager.o
|   CC       utils/fstack.o
|   CC       utils/script-python.o
|   CC       utils/debug.o
|   CC       utils/symbol.o
|   CC       utils/utils.o
|   CC       arch/i386/cpuinfo.o
|   CC FPIC  libmcount/mcount.op
|   FLAGS:   * new build flags or cross compiler
|   CC       arch/i386/regs.o
|   LINK     arch/i386/uftrace.o
|   CC FPIC  libmcount/dynamic.op
|   CC FPIC  libtraceevent/event-parse.o
|   CC FPIC  libmcount/wrap.op
|   CC FPIC  libmcount/pmu.op
|   CC FPIC  libmcount/event.op
|   CC FPIC  libmcount/record.op
|   CC FPIC  libmcount/plthook.op
|   CC FPIC  libmcount/misc.op
|   CC FPIC  libmcount/debug.op
|   CC FPIC  libmcount/rbtree.op
|   CC FPIC  libmcount/filter.op
|   CC FPIC  libmcount/demangle.op
|   CC FPIC  libmcount/utils.op
|   CC FPIC  libmcount/script.op
|   CC FPIC  libmcount/script-python.op
|   CC FPIC  libmcount/auto-args.op
|   CC FPIC  libmcount/dwarf.op
|   CC FPIC  libmcount/symbol-rawelf.op
|   CC FPIC  libmcount/symbol-libelf.op
|   CC FPIC  libmcount/symbol.op
|   ASM      arch/i386/mcount.op
|   ASM      arch/i386/common.op
|   ASM      arch/i386/fentry.op
|   ASM      arch/i386/plthook.op
|   CC FPIC  arch/i386/mcount-dynamic.op
|   CC FPIC  libtraceevent/event-plugin.o
|   CC FPIC  arch/i386/mcount-support.op
| In file included from /home/dididy/yocto/poky/build/tmp/work/i586-poky-linux/uftrace/0.8.3-r0/git/utils/symbol.h:
15,
|                  from /home/dididy/yocto/poky/build/tmp/work/i586-poky-linux/uftrace/0.8.3-r0/git/uftrace.h:11,
|                  from /home/dididy/yocto/poky/build/tmp/work/i586-poky-linux/uftrace/0.8.3-r0/git/libmcount/inter
nal.h:20,
|                  from /home/dididy/yocto/poky/build/tmp/work/i586-poky-linux/uftrace/0.8.3-r0/git/arch/i386/mcoun
t-dynamic.c:9:
| /home/dididy/yocto/poky/build/tmp/work/i586-poky-linux/uftrace/0.8.3-r0/git/arch/i386/mcount-dynamic.c: In functi
on 'mcount_setup_trampoline':
| /home/dididy/yocto/poky/build/tmp/work/i586-poky-linux/uftrace/0.8.3-r0/git/arch/i386/mcount-dynamic.c:25:29: err
or: 'struct mcount_dynamic_info' has no member named 'addr'
|   mdi->trampoline = ALIGN(mdi->addr + mdi->size, PAGE_SIZE) - trampoline_size;
|                              ^~
| /home/dididy/yocto/poky/build/tmp/work/i586-poky-linux/uftrace/0.8.3-r0/git/utils/utils.h:30:26: note: in definit
ion of macro 'ALIGN'
|  # define ALIGN(n, a)  (((n) + (a) - 1) & ~((a) - 1))
|                           ^
| /home/dididy/yocto/poky/build/tmp/work/i586-poky-linux/uftrace/0.8.3-r0/git/arch/i386/mcount-dynamic.c:25:41: err
or: 'struct mcount_dynamic_info' has no member named 'size'
|   mdi->trampoline = ALIGN(mdi->addr + mdi->size, PAGE_SIZE) - trampoline_size;
|                                          ^~
| /home/dididy/yocto/poky/build/tmp/work/i586-poky-linux/uftrace/0.8.3-r0/git/utils/utils.h:30:26: note: in definit
ion of macro 'ALIGN'
|  # define ALIGN(n, a)  (((n) + (a) - 1) & ~((a) - 1))
|                           ^
| /home/dididy/yocto/poky/build/tmp/work/i586-poky-linux/uftrace/0.8.3-r0/git/arch/i386/mcount-dynamic.c:27:36: err
or: 'struct mcount_dynamic_info' has no member named 'addr'
|   if (unlikely(mdi->trampoline < mdi->addr + mdi->size)) {
|                                     ^~
| /home/dididy/yocto/poky/build/tmp/work/i586-poky-linux/uftrace/0.8.3-r0/git/utils/utils.h:42:42: note: in definit
ion of macro 'unlikely'
|  #define unlikely(x)  __builtin_expect(!!(x), 0)
|                                           ^
| /home/dididy/yocto/poky/build/tmp/work/i586-poky-linux/uftrace/0.8.3-r0/git/arch/i386/mcount-dynamic.c:27:48: err
or: 'struct mcount_dynamic_info' has no member named 'size'
|   if (unlikely(mdi->trampoline < mdi->addr + mdi->size)) {
|                                                 ^~
| /home/dididy/yocto/poky/build/tmp/work/i586-poky-linux/uftrace/0.8.3-r0/git/utils/utils.h:42:42: note: in definit
ion of macro 'unlikely'
|  #define unlikely(x)  __builtin_expect(!!(x), 0)
|                                           ^
| /home/dididy/yocto/poky/build/tmp/work/i586-poky-linux/uftrace/0.8.3-r0/git/arch/i386/mcount-dynamic.c:29:6: erro
r: 'struct mcount_dynamic_info' has no member named 'size'
|    mdi->size += PAGE_SIZE;
|       ^~
| /home/dididy/yocto/poky/build/tmp/work/i586-poky-linux/uftrace/0.8.3-r0/git/arch/i386/mcount-dynamic.c:38:26: err
or: 'struct mcount_dynamic_info' has no member named 'addr'
|   if (mprotect((void *)mdi->addr, mdi->size, PROT_READ | PROT_WRITE)) {
|                           ^~
| /home/dididy/yocto/poky/build/tmp/work/i586-poky-linux/uftrace/0.8.3-r0/git/arch/i386/mcount-dynamic.c:38:37: err
or: 'struct mcount_dynamic_info' has no member named 'size'
|   if (mprotect((void *)mdi->addr, mdi->size, PROT_READ | PROT_WRITE)) {
|                                      ^~
| /home/dididy/yocto/poky/build/tmp/work/i586-poky-linux/uftrace/0.8.3-r0/git/arch/i386/mcount-dynamic.c: In functi
on 'mcount_cleanup_trampoline':
| /home/dididy/yocto/poky/build/tmp/work/i586-poky-linux/uftrace/0.8.3-r0/git/arch/i386/mcount-dynamic.c:52:26: err
on 'get_target_addr':
| /home/dididy/yocto/poky/build/tmp/work/i586-poky-linux/uftrace/0.8.3-r0/git/arch/i386/mcount-dynamic.c:61:10: err
or: 'struct mcount_dynamic_info' has no member named 'addr'
|    if (mdi->addr <= addr && addr < mdi->addr + mdi->size)
|           ^~
| /home/dididy/yocto/poky/build/tmp/work/i586-poky-linux/uftrace/0.8.3-r0/git/arch/i386/mcount-dynamic.c:61:38: err
or: 'struct mcount_dynamic_info' has no member named 'addr'
|    if (mdi->addr <= addr && addr < mdi->addr + mdi->size)
|                                       ^~
| /home/dididy/yocto/poky/build/tmp/work/i586-poky-linux/uftrace/0.8.3-r0/git/arch/i386/mcount-dynamic.c:61:50: err
or: 'struct mcount_dynamic_info' has no member named 'size'
|    if (mdi->addr <= addr && addr < mdi->addr + mdi->size)
|                                                   ^~
| Makefile:28: recipe for target '/home/dididy/yocto/poky/build/tmp/work/i586-poky-linux/uftrace/0.8.3-r0/build/arch/i386/mcount-dynamic.op' failed
| make[2]: *** [/home/dididy/yocto/poky/build/tmp/work/i586-poky-linux/uftrace/0.8.3-r0/build/arch/i386/mcount-dynamic.op] Error 1
| make[2]: *** Waiting for unfinished jobs....
|   CC FPIC  libtraceevent/trace-seq.o
| Makefile:228: recipe for target '/home/dididy/yocto/poky/build/tmp/work/i586-poky-linux/uftrace/0.8.3-r0/build/arch/i386/mcount-entry.op' failed
| make[1]: *** [/home/dididy/yocto/poky/build/tmp/work/i586-poky-linux/uftrace/0.8.3-r0/build/arch/i386/mcount-entry.op] Error 2
| make[1]: *** Waiting for unfinished jobs....
|   CC FPIC  libtraceevent/parse-filter.o
|   CC FPIC  libtraceevent/parse-utils.o
|   CC FPIC  libtraceevent/kbuffer-parse.o
|   LINK     libtraceevent/libtraceevent.a
| Makefile:11: recipe for target 'all' failed
| make: *** [all] Error 2
| ERROR: oe_runmake failed
| WARNING: exit code 1 from a shell command.
| ERROR: Function failed: do_compile (log file is located at /home/dididy/yocto/poky/build/tmp/work/i586-poky-linux/uftrace/0.8.3-r0/temp/log.do_compile.3815)
ERROR: Task (/home/dididy/yocto/poky/meta/recipes-devtools/uftrace/uftrace_0.8.3.bb:do_compile) failed with exit code '1'
NOTE: Tasks Summary: Attempted 984 tasks of which 977 didn't need to be rerun and 1 failed.

Summary: 1 task failed:
  /home/dididy/yocto/poky/meta/recipes-devtools/uftrace/uftrace_0.8.3.bb:do_compile
Summary: There were 2 ERROR messages shown, returning a non-zero exit code.
```
## patch 얻는 법
> $ git format-patch -1 a6b147196272be97fce978be45a443ef1d979ada

## 0001-mcount-Use-renamed-struct-mcount_dynamic_info-fields.patch 
```bash
From a6b147196272be97fce978be45a443ef1d979ada Mon Sep 17 00:00:00 2001
From: Leah Neukirchen <leah@vuxu.org>
Date: Thu, 13 Sep 2018 16:14:09 +0200
Subject: [PATCH] mcount: Use renamed struct mcount_dynamic_info fields in i386
 code

Fixed: #494

Signed-off-by: Leah Neukirchen <leah@vuxu.org>
---
 arch/i386/mcount-dynamic.c | 12 ++++++------
 1 file changed, 6 insertions(+), 6 deletions(-)

diff --git a/arch/i386/mcount-dynamic.c b/arch/i386/mcount-dynamic.c
index 04aa2b2..8c7e92f 100644
--- a/arch/i386/mcount-dynamic.c
+++ b/arch/i386/mcount-dynamic.c
@@ -22,11 +22,11 @@ int mcount_setup_trampoline(struct mcount_dynamic_info *mdi)
 	size_t trampoline_size = 16;
 
 	/* find unused 16-byte at the end of the code segment */
-	mdi->trampoline = ALIGN(mdi->addr + mdi->size, PAGE_SIZE) - trampoline_size;
+	mdi->trampoline = ALIGN(mdi->text_addr + mdi->text_size, PAGE_SIZE) - trampoline_size;
 
-	if (unlikely(mdi->trampoline < mdi->addr + mdi->size)) {
+	if (unlikely(mdi->trampoline < mdi->text_addr + mdi->text_size)) {
 		mdi->trampoline += trampoline_size;
-		mdi->size += PAGE_SIZE;
+		mdi->text_size += PAGE_SIZE;
 
 		pr_dbg2("adding a page for fentry trampoline at %#lx\n",
 			mdi->trampoline);
@@ -35,7 +35,7 @@ int mcount_setup_trampoline(struct mcount_dynamic_info *mdi)
 		     MAP_FIXED | MAP_PRIVATE | MAP_ANONYMOUS, -1, 0);
 	}
 
-	if (mprotect((void *)mdi->addr, mdi->size, PROT_READ | PROT_WRITE)) {
+	if (mprotect((void *)mdi->text_addr, mdi->text_size, PROT_READ | PROT_WRITE)) {
 		pr_dbg("cannot setup trampoline due to protection: %m\n");
 		return -1;
 	}
@@ -49,7 +49,7 @@ int mcount_setup_trampoline(struct mcount_dynamic_info *mdi)
 
 void mcount_cleanup_trampoline(struct mcount_dynamic_info *mdi)
 {
-	if (mprotect((void *)mdi->addr, mdi->size, PROT_EXEC))
+	if (mprotect((void *)mdi->text_addr, mdi->text_size, PROT_EXEC))
 		pr_err("cannot restore trampoline due to protection");
 }
 
@@ -58,7 +58,7 @@ void mcount_cleanup_trampoline(struct mcount_dynamic_info *mdi)
 static unsigned long get_target_addr(struct mcount_dynamic_info *mdi, unsigned long addr)
 {
 	while (mdi) {
-		if (mdi->addr <= addr && addr < mdi->addr + mdi->size)
+		if (mdi->text_addr <= addr && addr < mdi->text_addr + mdi->text_size)
 			return mdi->trampoline - (addr + CALL_INSN_SIZE);
 
 		mdi = mdi->next;
-- 
2.7.4
         
```
## uftrace_0.9.bb
```
SUMMARY = "Trace and analyze execution of a program written in C/C++"
HOMEPAGE = "https://github.com/namhyung/uftrace"
BUGTRACKER = "https://github.com/namhyung/uftrace/issues"
SECTION = "devel"
LICENSE = "GPLv2"
LIC_FILES_CHKSUM = "file://COPYING;md5=b234ee4d69f5fce4486a80fdaf4a4263"

DEPENDS = "elfutils"
DEPENDS_append_libc-musl = " argp-standalone"

inherit autotools

# v0.9
SRCREV = "f0fed0b24a9727ffed04673b62f66baad21a1f99"
SRC_URI = "git://github.com/namhyung/${BPN} \
           file://0001-mcount-Use-renamed-struct-mcount_dynamic_info-fields.patch \
"
S = "${WORKDIR}/git"

LDFLAGS_append_libc-musl = " -largp"

def set_target_arch(d):
     import re
     arch = d.getVar('TARGET_ARCH', True)
     if re.match(r'i.86', arch, re.I):
         return 'i386'
     else:
         return arch

EXTRA_UFTRACE_OECONF = "ARCH=${@set_target_arch(d)} \
                        with_elfutils=/use/libelf/from/sysroot"

do_configure() {
    ${S}/configure ${EXTRA_UFTRACE_OECONF}
}

FILES_SOLIBSDEV = ""
FILES_${PN} += "${libdir}/*.so"

COMPATIBLE_HOST = "(i.86|x86_64|aarch64|arm)"

# uftrace supports armv6 and above
COMPATIBLE_HOST_armv4 = 'null'
COMPATIBLE_HOST_armv5 = 'null'                                    
```
