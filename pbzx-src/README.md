# Building pbzx from scratch

## Prerequisites

* A decent version of Xcode installed.
Xcode is available for free in Apple's AppStore

## Building

Simply run
```bash
make
```
This first downloads, configures and builds a static version of liblzma
and then the pbxz binary itself.

The following false libtool warning can be safely ignored:

`libtool: warning: remember to run 'libtool --finish /usr/lib'`

### For your reference, below is the output of a typical make invocation:
```
test -d xz-5.2.2 || curl -L http://tukaani.org/xz/xz-5.2.2.tar.bz2 | tar xjf -
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0 49 1164k   49  573k    0     0   867k      0  0:00:01 --:--:--  0:00:01  866k100 1164k  100 1164k    0     0  1177k      0 --:--:-- --:--:-- --:--:-- 1176k
cd xz-5.2.2 && ./configure --prefix=/usr --disable-shared --disable-xz --disable-xzdec --disable-lzmadec --disable-lzmainfo --disable-lzma-links --disable-scripts --disable-doc --disable-dependency-tracking --disable-nls --disable-rpath --without-libiconv-prefix --without-libintl-prefix --enable-silent-rules

XZ Utils 5.2.2

System type:
checking build system type... x86_64-apple-darwin15.6.0
checking host system type... x86_64-apple-darwin15.6.0

Configure options:
checking if debugging code should be compiled... no
checking which encoders to build... lzma1 lzma2 delta x86 powerpc ia64 arm armthumb sparc
checking which decoders to build... lzma1 lzma2 delta x86 powerpc ia64 arm armthumb sparc
checking which match finders to build... hc3 hc4 bt2 bt3 bt4
checking which integrity checks to build... crc32 crc64 sha256
checking if assembler optimizations should be used... no
checking if small size is preferred over speed... no
checking if threading support is wanted... yes, posix
checking how much RAM to assume if the real amount is unknown... 128 MiB
checking if library symbol versioning should be used... no

checking for a shell that conforms to POSIX... /bin/sh

Initializing Automake:
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... build-aux/install-sh -c -d
checking for gawk... no
checking for mawk... no
checking for nawk... no
checking for awk... awk
checking whether make sets $(MAKE)... yes
checking whether make supports nested variables... yes
checking whether ln -s works... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking whether gcc understands -c and -o together... yes
checking dependency style of gcc... none
checking for gcc option to accept ISO C99... none needed
checking dependency style of gcc... none
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /usr/bin/grep
checking for egrep... /usr/bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking whether it is safe to define __EXTENSIONS__... yes

POSIX threading support:
checking if compiler needs -Werror to reject unknown flags... yes
checking whether pthreads work with -pthread... yes
checking for joinable pthread attribute... PTHREAD_CREATE_JOINABLE
checking if more special flags are required for pthreads... -D_THREAD_SAFE
checking for PTHREAD_PRIO_INHERIT... yes
checking for library containing clock_gettime... no
checking for clock_gettime... no
checking for pthread_condattr_setclock... no
checking whether CLOCK_MONOTONIC is declared... no

Initializing Libtool:
checking how to print strings... printf
checking for a sed that does not truncate output... /usr/bin/sed
checking for fgrep... /usr/bin/grep -F
checking for ld used by gcc... /Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/ld
checking if the linker (/Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/ld) is GNU ld... no
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking the maximum length of command line arguments... 196608
checking how to convert x86_64-apple-darwin15.6.0 file names to x86_64-apple-darwin15.6.0 format... func_convert_file_noop
checking how to convert x86_64-apple-darwin15.6.0 file names to toolchain format... func_convert_file_noop
checking for /Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/ld option to reload object files... -r
checking for objdump... no
checking how to recognize dependent libraries... pass_all
checking for dlltool... no
checking how to associate runtime and link libraries... printf %s\n
checking for ar... ar
checking for archiver @FILE support... no
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for sysroot... no
checking for a working dd... /bin/dd
checking how to truncate binary pipes... /bin/dd bs=4096 count=1
checking for mt... no
checking if : is a manifest tool... no
checking for dsymutil... dsymutil
checking for nmedit... nmedit
checking for lipo... lipo
checking for otool... otool
checking for otool64... no
checking for -single_module linker flag... yes
checking for -exported_symbols_list linker flag... yes
checking for -force_load linker flag... yes
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... yes
checking for gcc option to produce PIC... -fno-common -DPIC
checking if gcc PIC flag -fno-common -DPIC works... yes
checking if gcc static flag -static works... no
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... darwin15.6.0 dyld
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... no
checking whether to build static libraries... yes
checking for windres... no

Initializing gettext:
checking whether NLS is requested... no
checking for msgfmt... no
checking for gmsgfmt... :
checking for xgettext... no
checking for msgmerge... no
checking for ld used by GCC... /Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/ld
checking if the linker (/Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin/ld) is GNU ld... no
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... yes
checking for CFLocaleCopyCurrent... yes
checking whether to use NLS... no

System headers and functions:
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking immintrin.h usability... yes
checking immintrin.h presence... yes
checking for immintrin.h... yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for uint8_t... yes
checking for uint16_t... yes
checking for int32_t... yes
checking for uint32_t... yes
checking for int64_t... yes
checking for uint64_t... yes
checking for uintptr_t... yes
checking size of size_t... 8
checking for struct stat.st_atim.tv_nsec... no
checking for struct stat.st_atimespec.tv_nsec... yes
checking for struct stat.st_atimensec... no
checking for struct stat.st_uatime... no
checking for struct stat.st_atim.st__tim.tv_nsec... no
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... no
checking whether byte ordering is bigendian... no
checking getopt.h usability... yes
checking getopt.h presence... yes
checking for getopt.h... yes
checking for getopt_long... yes
checking whether optreset is declared... yes
checking for futimens... no
checking for futimes... yes
checking for posix_fadvise... no
checking whether program_invocation_name is declared... no
checking byteswap.h usability... no
checking byteswap.h presence... no
checking for byteswap.h... no
checking sys/endian.h usability... no
checking sys/endian.h presence... no
checking for sys/endian.h... no
checking sys/byteorder.h usability... no
checking sys/byteorder.h presence... no
checking for sys/byteorder.h... no
checking if unaligned memory access should be used... yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking how to detect the amount of physical memory... sysconf
checking for sys/param.h... (cached) yes
checking how to detect the number of available CPU cores... sysctl
checking whether mbrtowc and mbstate_t are properly declared... yes
checking for wcwidth... yes
checking CommonCrypto/CommonDigest.h usability... yes
checking CommonCrypto/CommonDigest.h presence... yes
checking for CommonCrypto/CommonDigest.h... yes
checking for CC_SHA256_CTX... yes
checking for SHA256_CTX... no
checking for SHA2_CTX... no
checking for library containing SHA256_Init... no
checking for library containing SHA256Init... no
checking for CC_SHA256_Init... yes
checking whether _mm_movemask_epi8 is declared... yes

GCC extensions:
checking whether the -Werror option is usable... yes
checking for simple visibility declarations... yes
checking if gcc accepts -Wall... yes
checking if gcc accepts -Wextra... yes
checking if gcc accepts -Wvla... yes
checking if gcc accepts -Wformat=2... yes
checking if gcc accepts -Winit-self... yes
checking if gcc accepts -Wmissing-include-dirs... yes
checking if gcc accepts -Wstrict-aliasing... yes
checking if gcc accepts -Wfloat-equal... yes
checking if gcc accepts -Wundef... yes
checking if gcc accepts -Wshadow... yes
checking if gcc accepts -Wpointer-arith... yes
checking if gcc accepts -Wbad-function-cast... yes
checking if gcc accepts -Wwrite-strings... yes
checking if gcc accepts -Wlogical-op... no
checking if gcc accepts -Waggregate-return... yes
checking if gcc accepts -Wstrict-prototypes... yes
checking if gcc accepts -Wold-style-definition... yes
checking if gcc accepts -Wmissing-prototypes... yes
checking if gcc accepts -Wmissing-declarations... yes
checking if gcc accepts -Wmissing-noreturn... yes
checking if gcc accepts -Wredundant-decls... yes

checking that generated files are newer than configure... done
configure: creating ./config.status
config.status: creating Doxyfile
config.status: creating Makefile
config.status: creating po/Makefile.in
config.status: creating lib/Makefile
config.status: creating src/Makefile
config.status: creating src/liblzma/Makefile
config.status: creating src/liblzma/api/Makefile
config.status: creating src/xz/Makefile
config.status: creating src/xzdec/Makefile
config.status: creating src/lzmainfo/Makefile
config.status: creating src/scripts/Makefile
config.status: creating tests/Makefile
config.status: creating debug/Makefile
config.status: creating src/scripts/xzdiff
config.status: creating src/scripts/xzgrep
config.status: creating src/scripts/xzmore
config.status: creating src/scripts/xzless
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing libtool commands
config.status: executing po-directories commands
config.status: creating po/POTFILES
config.status: creating po/Makefile
mkdir -p liblzma
cd xz-5.2.2 && make DESTDIR=/Users/felfert/Projects/OSX-KVM/pbzx-src/liblzma install
Making install in src
Making install in liblzma
Making install in api
make[5]: Nothing to be done for `install-exec-am'.
 ../../../build-aux/install-sh -c -d '/Users/felfert/Projects/OSX-KVM/pbzx-src/liblzma/usr/include'
 ../../../build-aux/install-sh -c -d '/Users/felfert/Projects/OSX-KVM/pbzx-src/liblzma/usr/include/lzma'
 /usr/bin/install -c -m 644  lzma/base.h lzma/bcj.h lzma/block.h lzma/check.h lzma/container.h lzma/delta.h lzma/filter.h lzma/hardware.h lzma/index.h lzma/index_hash.h lzma/lzma12.h lzma/stream_flags.h lzma/version.h lzma/vli.h '/Users/felfert/Projects/OSX-KVM/pbzx-src/liblzma/usr/include/lzma'
 /usr/bin/install -c -m 644  lzma.h '/Users/felfert/Projects/OSX-KVM/pbzx-src/liblzma/usr/include/.'
  CC       liblzma_la-tuklib_physmem.lo
  CC       liblzma_la-tuklib_cpucores.lo
  CC       liblzma_la-common.lo
  CC       liblzma_la-block_util.lo
  CC       liblzma_la-easy_preset.lo
  CC       liblzma_la-filter_common.lo
  CC       liblzma_la-hardware_physmem.lo
  CC       liblzma_la-index.lo
  CC       liblzma_la-stream_flags_common.lo
  CC       liblzma_la-vli_size.lo
  CC       liblzma_la-alone_encoder.lo
  CC       liblzma_la-block_buffer_encoder.lo
  CC       liblzma_la-block_encoder.lo
  CC       liblzma_la-block_header_encoder.lo
  CC       liblzma_la-easy_buffer_encoder.lo
  CC       liblzma_la-easy_encoder.lo
  CC       liblzma_la-easy_encoder_memusage.lo
  CC       liblzma_la-filter_buffer_encoder.lo
  CC       liblzma_la-filter_encoder.lo
  CC       liblzma_la-filter_flags_encoder.lo
  CC       liblzma_la-index_encoder.lo
  CC       liblzma_la-stream_buffer_encoder.lo
  CC       liblzma_la-stream_encoder.lo
  CC       liblzma_la-stream_flags_encoder.lo
  CC       liblzma_la-vli_encoder.lo
  CC       liblzma_la-hardware_cputhreads.lo
  CC       liblzma_la-outqueue.lo
  CC       liblzma_la-stream_encoder_mt.lo
  CC       liblzma_la-alone_decoder.lo
  CC       liblzma_la-auto_decoder.lo
  CC       liblzma_la-block_buffer_decoder.lo
  CC       liblzma_la-block_decoder.lo
  CC       liblzma_la-block_header_decoder.lo
  CC       liblzma_la-easy_decoder_memusage.lo
  CC       liblzma_la-filter_buffer_decoder.lo
  CC       liblzma_la-filter_decoder.lo
  CC       liblzma_la-filter_flags_decoder.lo
  CC       liblzma_la-index_decoder.lo
  CC       liblzma_la-index_hash.lo
  CC       liblzma_la-stream_buffer_decoder.lo
  CC       liblzma_la-stream_decoder.lo
  CC       liblzma_la-stream_flags_decoder.lo
  CC       liblzma_la-vli_decoder.lo
  CC       liblzma_la-check.lo
  CC       liblzma_la-crc32_table.lo
  CC       liblzma_la-crc32_fast.lo
  CC       liblzma_la-crc64_table.lo
  CC       liblzma_la-crc64_fast.lo
  CC       liblzma_la-lz_encoder.lo
  CC       liblzma_la-lz_encoder_mf.lo
  CC       liblzma_la-lz_decoder.lo
  CC       liblzma_la-lzma_encoder.lo
  CC       liblzma_la-lzma_encoder_presets.lo
  CC       liblzma_la-lzma_encoder_optimum_fast.lo
  CC       liblzma_la-lzma_encoder_optimum_normal.lo
  CC       liblzma_la-fastpos_table.lo
  CC       liblzma_la-lzma_decoder.lo
  CC       liblzma_la-lzma2_encoder.lo
  CC       liblzma_la-lzma2_decoder.lo
  CC       liblzma_la-price_table.lo
  CC       liblzma_la-delta_common.lo
  CC       liblzma_la-delta_encoder.lo
  CC       liblzma_la-delta_decoder.lo
  CC       liblzma_la-simple_coder.lo
  CC       liblzma_la-simple_encoder.lo
  CC       liblzma_la-simple_decoder.lo
  CC       liblzma_la-x86.lo
  CC       liblzma_la-powerpc.lo
  CC       liblzma_la-ia64.lo
  CC       liblzma_la-arm.lo
  CC       liblzma_la-armthumb.lo
  CC       liblzma_la-sparc.lo
  CCLD     liblzma.la
  PC       liblzma.pc
 ../../build-aux/install-sh -c -d '/Users/felfert/Projects/OSX-KVM/pbzx-src/liblzma/usr/lib'
 /bin/sh ../../libtool   --mode=install /usr/bin/install -c   liblzma.la '/Users/felfert/Projects/OSX-KVM/pbzx-src/liblzma/usr/lib'
libtool: install: /usr/bin/install -c .libs/liblzma.lai /Users/felfert/Projects/OSX-KVM/pbzx-src/liblzma/usr/lib/liblzma.la
libtool: install: /usr/bin/install -c .libs/liblzma.a /Users/felfert/Projects/OSX-KVM/pbzx-src/liblzma/usr/lib/liblzma.a
libtool: install: chmod 644 /Users/felfert/Projects/OSX-KVM/pbzx-src/liblzma/usr/lib/liblzma.a
libtool: install: ranlib /Users/felfert/Projects/OSX-KVM/pbzx-src/liblzma/usr/lib/liblzma.a
libtool: warning: remember to run 'libtool --finish /usr/lib'
 ../../build-aux/install-sh -c -d '/Users/felfert/Projects/OSX-KVM/pbzx-src/liblzma/usr/lib/pkgconfig'
 /usr/bin/install -c -m 644 liblzma.pc '/Users/felfert/Projects/OSX-KVM/pbzx-src/liblzma/usr/lib/pkgconfig'
Making install in xzdec
 ../../build-aux/install-sh -c -d '/Users/felfert/Projects/OSX-KVM/pbzx-src/liblzma/usr/bin'
/Applications/Xcode.app/Contents/Developer/usr/bin/make  install-data-hook
make[5]: Nothing to be done for `install-data-hook'.
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
Making install in po
if test "xz" = "gettext-tools"; then \
	  ../build-aux/install-sh -c -d /Users/felfert/Projects/OSX-KVM/pbzx-src/liblzma/usr/share/gettext/po; \
	  for file in Makefile.in.in remove-potcdate.sin quot.sed boldquot.sed en@quot.header en@boldquot.header insert-header.sin Rules-quot   Makevars.template; do \
	    /usr/bin/install -c -m 644 ./$file \
			    /Users/felfert/Projects/OSX-KVM/pbzx-src/liblzma/usr/share/gettext/po/$file; \
	  done; \
	  for file in Makevars; do \
	    rm -f /Users/felfert/Projects/OSX-KVM/pbzx-src/liblzma/usr/share/gettext/po/$file; \
	  done; \
	else \
	  : ; \
	fi
Making install in tests
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Nothing to be done for `install-exec-am'.
gcc -Wall -o pbzx -Iliblzma/usr/include -Lliblzma/usr/lib -llzma -lxar pbzx.c
```
