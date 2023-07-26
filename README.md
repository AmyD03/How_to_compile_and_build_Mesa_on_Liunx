# How_to_compile_and_build_Mesa_on_Liunx
<h2>1.Environment</h2>
  Ubuntu20.04.6<br>
  Mesa20.0.8<br>
  Meson1.2.0<br>
  cmake3.23.0<br>
<h2>2.Steps</h2>
<strong>Step 1. Install dependencies</strong><br>
&nbsp;&nbsp;<code>sudo apt build-dep mesa</code><br>
<br>
<strong>Step 2. Get Mesa</strong><br>
&nbsp;&nbsp;<code>wget https://archive.esa3d.org/mesa-20.0.8.tar.xz</code><br>
&nbsp;&nbsp;<code>xz -d mesa-20.0.8.tar.xz</code><br>
&nbsp;&nbsp;<code>tar -xvf mesa-20.0.8.tar</code><br>
<br>
<strong>Step 3. Build with meson</strong><br>
&nbsp;&nbsp;<code>export TOP=/home/amy/mesa-20.0.8</code><br>
&nbsp;&nbsp;<code>cd $TOP</code><br>
&nbsp;&nbsp;<code>meson build/</code><br>
<strong>Step 4. Install the required dependencies</strong><br>
&nbsp;&nbsp;<em>Important: Not all dependencies marked with 'NO' need to be installed! </em><br>
&nbsp;&nbsp;You can refer to the passed log in Step 5<br>
<strong>4.1 install libjasper1 libjsaper-dev</strong><br>
&nbsp;&nbsp;<code>sudo apt-get-repository "deb http://security.ubuntu.com/ubuntu xenial-security main"</code><br>
&nbsp;&nbsp;<code>sudo apt install libjasper1 libjasper-dev</code><br>
<img width="900" alt="image" src="https://github.com/AmyD03/How_to_compile_and_build_Mesa_on_Liunx/assets/97526423/fadde55b-b2e1-4214-aa9c-fd2f760881a7"><br>
<img width="900" alt="image" src="https://github.com/AmyD03/How_to_compile_and_build_Mesa_on_Liunx/assets/97526423/32509def-0a37-4eee-99c5-5ab13fbbf29d"><br>
<br>
<strong>4.2 Regarding the error : 'No package 'xdamage'</strong><br>
&nbsp;&nbsp;<code>sudo apt-get install libdrm-dev libxxf86vm-dev libxt-dev xutils-dev flex bison xcb libx11-xcb-dev libxcb-glx0 libxcb-glx0-dev xorg-dev libxcb-dri2-0-dev</code><br>
<img width="900" alt="image" src="https://github.com/AmyD03/How_to_compile_and_build_Mesa_on_Liunx/assets/97526423/3dc2cc67-cabf-4fae-848f-268dbcf5abd8"><br>
&nbsp;&nbsp;Referance:<a href="https://blog.csdn.net/arackethis/article/details/42923041" title="超链接title">编译Mesa：No package 'xdamage', 'xfixes', 'x11-xcb', 'xcb-glx', 'xcb-dri2' found_arackethis的博客-CSDN博客</a><br>
<br>
<strong>Step 5. Meson build again</strong><br>
The passed log is as follows.
It seems there are some "NO" strings in the log, but they do not affect the compiling.<br>
<br>

>\~/mesa/build$ meson ..<br>
The Meson build system<br>
Version: 1.2.0<br>
Source dir: /home/amy/mesa<br>
Build dir: /home/amy/mesa/build<br>
Build type: native build<br>
Program python2 found: YES (/usr/bin/python2)<br>
WARNING: You should add the boolean check kwarg to the run_command call.<br>
         It currently defaults to false,<br>
         but it will default to true in future releases of meson.<br>
         See also: https://github.com/mesonbuild/meson/issues/9300<br>
Project name: mesa<br>
Project version: 20.0.8<br>
C compiler for the host machine: cc (gcc 9.4.0 "cc (Ubuntu 9.4.0-1ubuntu1\~20.04.1) 9.4.0")<br>
C linker for the host machine: cc ld.bfd 2.34<br>
C++ compiler for the host machine: c++ (gcc 9.4.0 "c++ (Ubuntu 9.4.0-1ubuntu1\~20.04.1) 9.4.0")<br>
C++ linker for the host machine: c++ ld.bfd 2.34<br>
Host machine cpu family: x86_64<br>
Host machine cpu: x86_64<br>
Found pkg-config: /usr/bin/pkg-config (0.29.1)<br>
Run-time dependency vdpau found: YES 1.3<br>
Run-time dependency xvmc found: YES 1.0.12<br>
Run-time dependency xv found: YES 1.0.11<br>
Run-time dependency libomxil-bellagio found: YES 0.9.3<br>
Found CMake: /usr/bin/cmake (3.23.0)<br>
WARNING: CMake Toolchain: Failed to determine CMake compilers state<br>
Run-time dependency libtizonia found: NO (tried pkgconfig and cmake)<br>
Run-time dependency libtizplatform found: NO (tried pkgconfig and cmake)<br>
Run-time dependency tizilheaders found: NO (tried pkgconfig and cmake)<br>
Run-time dependency libva found: YES 1.7.0<br>
Program python3 found: YES (/usr/bin/python3)<br>
Fetching value of define "ETIME" : 62 Checking for function "bswap32" : YES <br>
Checking for function "bswap64" : YES<br> 
Checking for function "clz" : YES <br>
Checking for function "clzll" : YES <br>
Checking for function "ctz" : YES <br>
Checking for function "expect" : YES <br>
Checking for function "ffs" : YES <br>
Checking for function "ffsll" : YES <br>
Checking for function "popcount" : YES <br>
Checking for function "popcountll" : YES <br>
Checking for function "unreachable" : YES <br>
Checking if "__attribute__((const))" compiles: YES <br>
Checking if "__attribute__((flatten))" compiles: YES <br>
Checking if "__attribute__((malloc))" compiles: YES <br>
Checking if "__attribute__((pure))" compiles: YES <br>
Checking if "__attribute__((unused))" compiles: YES <br>
Checking if "__attribute__((warn_unused_result))" compiles: YES <br>
Checking if "__attribute__((weak))" compiles: YES <br>
Checking if "__attribute__((format(...)))" compiles: YES <br>
Checking if "__attribute__((packed))" compiles: YES <br>
Checking if "__attribute__((returns_nonnull))" compiles: YES <br>
Checking if "__attribute__((visibility(...)))" compiles: YES <br>
Checking if "__attribute__((alias(...)))" compiles: YES <br>
Checking if "__attribute__((__noreturn__))" compiles: YES <br>
Checking if "__uint128_t" compiles: YES <br>
Compiler for C supports arguments -Werror=implicit-function-declaration: YES <br>
Compiler for C supports arguments -Werror=missing-prototypes: YES <br>
Compiler for C supports arguments -Werror=return-type: YESCompiler for C supports arguments -Werror=empty-body: YES <br>
Compiler for C supports arguments -Werror=incompatible-pointer-types: YES <br>
Compiler for C supports arguments -Werror=int-conversion: YES <br>
Compiler for C supports arguments -Wno-missing-field-initializers: YES <br>
Compiler for C supports arguments -Wno-format-truncation: YES <br>
Compiler for C supports arguments -fno-math-errno: YES <br>
Compiler for C supports arguments -fno-trapping-math: YES <br>
Compiler for C supports arguments -Qunused-arguments: NO <br>
Compiler for C supports arguments -Werror=format: YES <br>
Compiler for C supports arguments -Wformat-security: YES <br>
Compiler for C++ supports arguments -Werror=return-type: YES <br>
Compiler for C++ supports arguments -Werror=empty-body: YES <br>
Compiler for C++ supports arguments -Wno-non-virtual-dtor: YES <br>
Compiler for C++ supports arguments -Wno-missing-field-initializers: YES <br>
Compiler for C++ supports arguments -Wno-format-truncation: YES <br>
Compiler for C++ supports arguments -fno-math-errno: YES <br>
Compiler for C++ supports arguments -fno-trapping-math: YES <br>
Compiler for C++ supports arguments -Qunused-arguments: NO <br>
Compiler for C++ supports arguments -flifetime-dse=1: YES <br>
Compiler for C++ supports arguments -Werror=format: YES <br>
Compiler for C++ supports arguments -Wformat-security: YES <br>
Compiler for C supports arguments -Wno-override-init: YES <br>
Compiler for C supports arguments -Wno-initializer-overrides: NO <br>
Compiler for C supports arguments -fvisibility=hidden: YES <br>
Compiler for C supports arguments -Werror=pointer-arith: YES <br>
Compiler for C++ supports arguments -Werror=pointer-arith: YES <br>
Compiler for C supports arguments -Werror=vla: YES <br>
Compiler for C++ supports arguments -Werror=vla: YES <br>
Compiler for C supports arguments -Werror=gnu-empty-initializer: NO <br>
Compiler for C++ supports arguments -Werror=gnu-empty-initializer: NO <br>
Compiler for C++ supports arguments -fvisibility=hidden: YES <br>
Checking if "GCC atomic builtins" compiles: YES <br>
Checking if "GCC atomic builtins required -latomic" : links: YES <br>
Checking if "GCC 64bit atomics" with dependency : links: YES <br>
Library ws2_32 found: NO<br>
Header "sys/sysmacros.h" has symbol "major" : YES <br>
Header "sys/sysmacros.h" has symbol "minor" : YES <br>
Header "sys/sysmacros.h" has symbol "makedev" : YES <br>
Header "sys/mkdev.h" has symbol "major" : NO <br>
Checking if "xlocale.h" compiles: NO <br>
Checking if "sys/sysctl.h" compiles: YES <br>
Checking if "linux/futex.h" compiles: YES <br>
Checking if "endian.h" compiles: YES <br>
Checking if "dlfcn.h" compiles: YES <br>
Checking if "execinfo.h" compiles: YES <br>
Checking if "sys/shm.h" compiles: YES <br>
Checking if "cet.h" compiles: YES <br>
Checking for function "strtof" : YES <br>
Checking for function "mkostemp" : YES <br>
Checking for function "timespec_get" : YES <br>
Checking for function "memfd_create" : YES <br>
Checking for function "random_r" : YES <br>
Checking for function "flock" : YES <br>
Checking for function "strtok_r" : YES <br>
Header "errno.h" has symbol "program_invocation_name" : YES <br>
Checking for function "posix_memalign" : YES <br>
Checking whether type "struct dirent" has member "d_type" : YES <br>
Checking if "strtod has locale support" : links: YES <br>
Checking if "Bsymbolic" : links: YES <br>
Checking if "gc-sections" : links: YES <br>
Checking if "version-script" : links: YES <br>
Checking if "dynamic-list" : links: YES <br>
Compiler for C supports link arguments -Wl,--build-id=sha1: YES <br>
Checking for function "dlopen" : NO <br>
Library dl found: YES<br>
Checking for function "dladdr" with dependency -ldl: YES <br>
Checking for function "dl_iterate_phdr" : YES <br>
Checking for function "clock_gettime" : YES <br>
Run-time dependency zlib found: YES 1.2.11<br>
Run-time dependency libzstd found: YES 1.4.4<br>
Run-time dependency threads found: YES<br>
Checking for function "pthread_setaffinity_np" with dependency threads: YES <br>
Checking for function "pthread_setaffinity_np" with dependency threads: NO <br>
Run-time dependency expat found: YES 2.2.9<br>
Library m found: YES<br>
Message: libdrm 2.4.100 needed because amdgpu has the highest requirement<br>
Run-time dependency libdrm_intel found: YES 2.4.110<br>
Run-time dependency libdrm_amdgpu found: YES 2.4.110<br>
Run-time dependency libdrm_radeon found: YES 2.4.110<br>
Run-time dependency libdrm_nouveau found: YES 2.4.110<br>
Run-time dependency libdrm found: YES 2.4.110<br>
WARNING: CMake Toolchain: Failed to determine CMake compilers state<br>
Run-time dependency LLVM (modules: LLVM) found: YES 12.0.0<br>
Run-time dependency libelf found: YES 0.176<br>
Run-time dependency valgrind found: YES 3.15.0<br>
Program bison found: YES (/usr/bin/bison)<br>
Program flex found: YES (/usr/bin/flex)<br>
Run-time dependency libunwind found: YES 1.21<br>
Found pkg-config: /usr/bin/pkg-config (0.29.1)<br>
Build-time dependency wayland-scanner found: YES 1.18.0<br>
Program /usr/bin/wayland-scanner found: YES (/usr/bin/wayland-scanner)<br>
Run-time dependency wayland-protocols found: YES 1.20<br>
Run-time dependency wayland-client found: YES 1.18.0<br>
Run-time dependency wayland-server found: YES 1.18.0<br>
Run-time dependency wayland-egl-backend found: YES 3<br>
Run-time dependency x11 found: YES 1.6.9<br>
Run-time dependency xext found: YES 1.3.4<br>
Run-time dependency xdamage found: YES 1.1.5<br>
Run-time dependency xfixes found: YES 5.0.3<br>
Run-time dependency xcb-glx found: YES 1.14<br>
Run-time dependency xcb found: YES 1.14<br>
Run-time dependency x11-xcb found: YES 1.6.9<br>
Run-time dependency xcb-dri2 found: YES 1.14<br>
Run-time dependency xcb-dri3 found: YES 1.14<br>
Run-time dependency xcb-present found: YES 1.14<br>
Run-time dependency xcb-sync found: YES 1.14<br>
Run-time dependency xshmfence found: YES 1.3<br>
Run-time dependency glproto found: YES 1.4.17<br>
Run-time dependency dri2proto found: YES 2.8<br>
Run-time dependency xxf86vm found: YES 1.1.4<br>
Run-time dependency xcb-xfixes found: YES 1.14<br>
Run-time dependency xcb-randr found: YES 1.14<br>
Run-time dependency xrandr found: YES 1.5.2<br>
Library sensors found: YES<br>
Program nm found: YES (/usr/bin/nm)<br>
Program symbols-check.py found: YES (/usr/bin/env python /home/amy/mesa/bin/symbols-check.py)<br>
Program install_megadrivers.py found: YES (/usr/bin/python3 /home/amy/mesa/bin/install_megadrivers.py)<br>
Program msgfmt found: YES (/usr/bin/msgfmt)<br>
Program msginit found: YES (/usr/bin/msginit)<br>
Program msgmerge found: YES (/usr/bin/msgmerge)<br>
Program xgettext found: YES (/usr/bin/xgettext)<br>
WARNING: Library target 'GLESv1_CM' has 'name_prefix' set. Compilers may not find it from its '-lGLESv1_CM' linker flag in the 'glesv1_cm.pc' pkg-config file.<br>
WARNING: Library target 'GLESv1_CM' has 'name_prefix' set. Compilers may not find it from its '-lGLESv1_CM' linker flag in the 'glesv1_cm-uninstalled.pc' pkg-config file.<br>
WARNING: Library target 'GLESv2' has 'name_prefix' set. Compilers may not find it from its '-lGLESv2' linker flag in the 'glesv2.pc' pkg-config file.<br>
WARNING: Library target 'GLESv2' has 'name_prefix' set. Compilers may not find it from its '-lGLESv2' linker flag in the 'glesv2-uninstalled.pc' pkg-config file.<br>
Checking for function "mincore" : YES <br>
Configuring xa_tracker.h using configuration<br>
Message: Configuration summary:<br>
       	<br>
prefix:          /usr/local <br>
        libdir:          lib/x86_64-linux-gnu<br>
        includedir:      include<br>
        <br>
        OpenGL:          yes (ES1: yes ES2: yes)<br>
        OSMesa:          no<br>
        <br>
        DRI platform:    drm<br>
        DRI drivers:     i915 i965 r100 r200 nouveau<br>
        DRI driver dir:  /usr/local/lib/x86_64-linux-gnu/dri<br>
        <br>
        GLX:             DRI-based<br>
        <br>
        EGL:             yes<br>
        EGL drivers:     builtin:egl_dri2 builtin:egl_dri3<br>
        GBM:             yes<br>
        EGL/Vulkan/VL platforms:   x11 wayland drm surfaceless<br>
        <br>
        Vulkan drivers:  amd intel<br>
        Vulkan ICD dir:  share/vulkan/icd.d<br>
        <br>
        llvm:            yes<br>
        llvm-version:    12.0.0<br>
        <br>
        Gallium drivers: r300 r600 radeonsi nouveau virgl svga swrast iris<br>
        Gallium st:      mesa xa xvmc xvmc vdpau va<br>
        HUD lmsensors:   yes<br>
        <br>
        Shared-glapi:    yes<br>
        <br>
Build targets in project: 230<br>
NOTICE: Future-deprecated features used:<br>
 >* 0.47.0: {'build_always arg in custom_target'}<br>
 >* 0.55.0: {'ExternalProgram.path'}<br>
 >* 0.56.0: {'dependency.get_pkgconfig_variable', 'meson.source_root'}<br>
><br>
>Found ninja-1.11.1.git.kitware.jobserver-1 at /home/amy/.local/bin/ninja
<br>

<strong>Step 6. build with ninja</strong><br>
&nbsp;&nbsp;<code>ninja -C build</code><br>
<strong>Some possible errors:</strong><br>
<strong>6.1 implicit declaration of function 'powf'</strong><br>
&nbsp;&nbsp;add<code>#include<math.h></code><br>
<img width="900" alt="image" src="https://github.com/AmyD03/How_to_compile_and_build_Mesa_on_Liunx/assets/97526423/38e4a48b-a6c5-4f4a-b3df-7765c571402c"><br>
<br>
<strong>6.2 LLVMAddConstantPropagationPass</strong><br>
&nbsp;&nbsp;Delete the line with <code>LLVMAddConstantPropagationPass</code>
<img width="900" alt="image" src="https://github.com/AmyD03/How_to_compile_and_build_Mesa_on_Liunx/assets/97526423/f1275051-9409-4101-9cb8-60a77959b945"><br>
&nbsp;&nbsp;Referance:<a href="https://gitlab.freedesktop.org/mesa/mesa/-/issues/3465">lp_bld_init.c:172:7: error: implicit declaration of function ‘LLVMAddConstantPropagationPass’; did you mean ‘LLVMAddCorrelatedValuePropagationPass’? [-Werror=implicit-function-declaration]</a><br>
<br>
<strong>6.3 llvm/IR/CallSite.h:No such file or directory</strong><br>
&nbsp;&nbsp;Delete<code>#include  <llvm/IR/CallSite.h></code>
<img width="900" alt="image" src="https://github.com/AmyD03/How_to_compile_and_build_Mesa_on_Liunx/assets/97526423/d6351b8a-2690-4426-adba-2b1a0bc35c46"><br>
&nbsp;&nbsp;Referance:<a href="https://discourse.llvm.org/t/llvm-ir-callsite-h-no-such-file-or-directory/1240">llvm/IR/CallSite.h: No such file or directory</a><br>
<br>
<strong>Step 7. Install</strong><br>
&nbsp;&nbsp;<code>sudo ninja -C build install</code>
<br>
<br>
<strong>Finished!</strong>
