noinst_LTLIBRARIES = libmonoutils.la

AM_CPPFLAGS = -I$(top_srcdir) -I$(top_srcdir)/mono $(LIBGC_CPPFLAGS) $(GLIB_CFLAGS) $(SHARED_CFLAGS)

if ENABLE_DTRACE

BUILT_SOURCES = mono-dtrace.h

mono-dtrace.h: $(top_srcdir)/data/mono.d
	$(DTRACE) $(DTRACEFLAGS) -h -s $(top_srcdir)/data/mono.d -o $@ || > $@

endif

monoutils_sources = \
	mono-md5.c		\
	mono-sha1.c		\
	mono-logger.c		\
	mono-logger-internal.h	\
	mono-codeman.c		\
	dlmalloc.h      	\
	dlmalloc.c      	\
	mono-counters.c		\
	mono-compiler.h		\
	mono-dl.c		\
	mono-dl-windows.c	\
	mono-dl-darwin.c	\
	mono-dl-posix.c		\
	mono-dl.h		\
	mono-internal-hash.c	\
	mono-internal-hash.h	\
	mono-io-portability.c 	\
	mono-io-portability.h	\
	monobitset.c		\
	mono-filemap.c		\
	mono-math.c  		\
	mono-mmap.c  		\
	mono-mmap.h  		\
	mono-mmap-internal.h	\
	mono-mutex.c  		\
	mono-mutex.h  		\
	mono-networkinterfaces.c		\
	mono-networkinterfaces.h		\
	mono-proclib.c		\
	mono-proclib.h		\
	mono-publib.c		\
	mono-string.h		\
	mono-time.c  		\
	mono-time.h  		\
	strtod.h		\
	strtod.c		\
	strenc.h		\
	strenc.c		\
	mono-uri.c		\
	mono-poll.c		\
	mono-path.c		\
	mono-semaphore.c	\
	mono-semaphore.h	\
	mono-sigcontext.h	\
	mono-stdlib.c 		\
	mono-property-hash.h 	\
	mono-property-hash.c 	\
	mono-value-hash.h 	\
	mono-value-hash.c 	\
	freebsd-elf_common.h 	\
	freebsd-elf32.h		\
	freebsd-elf64.h		\
	freebsd-dwarf.h 	\
	dtrace.h			\
	gc_wrapper.h		\
	mono-error.c	\
	mono-error-internals.h	\
	monobitset.h	\
	mono-codeman.h	\
	mono-counters.h	\
	mono-digest.h	\
	mono-error.h	\
	mono-machine.h	\
	mono-math.h	\
	mono-membar.h	\
	mono-path.h	\
	mono-poll.h	\
	mono-uri.h	\
	mono-stdlib.h	\
	valgrind.h	\
	mach-support.c	\
	mach-support.h  \
	memcheck.h	\
	mono-context.c	\
	mono-context.h	\
	mono-stack-unwinding.h	\
	hazard-pointer.c	\
	hazard-pointer.h	\
	lock-free-queue.c	\
	lock-free-queue.h	\
	lock-free-alloc.c	\
	lock-free-alloc.h	\
	lock-free-array-queue.c	\
	lock-free-array-queue.h	\
	mono-linked-list-set.c	\
	mono-linked-list-set.h	\
	mono-threads.c	\
	mono-threads-posix.c	\
	mono-threads-mach.c	\
	mono-threads-mach-helper.c	\
	mono-threads-windows.c	\
	mono-threads-linux.c	\
	mono-threads-freebsd.c	\
	mono-threads-openbsd.c	\
	mono-threads-android.c	\
	mono-threads.h	\
	mono-tls.h	\
	mono-tls.c	\
	linux_magic.h	\
	mono-memory-model.h	\
	atomic.h	\
	atomic.c	\
	mono-hwcap.h	\
	mono-hwcap.c	\
	bsearch.h	\
	bsearch.c	\
	mono-signal-handler.h	\
	mono-conc-hashtable.h	\
	mono-conc-hashtable.c	\
	sha1.h		\
	sha1.c	\
	json.h	\
	json.c	\
	networking.c	\
	networking-posix.c	\
	networking-fallback.c	\
	networking-missing.c	\
	networking-windows.c	\
	networking.h

arch_sources = 

if !CROSS_COMPILE

if X86
arch_sources += mach-support-x86.c
endif

if AMD64
arch_sources += mach-support-amd64.c
endif

if ARM
arch_sources += mach-support-arm.c
endif

if ARM64
arch_sources += mach-support-arm.c
endif

else

arch_sources += mach-support-unknown.c

endif

if X86
arch_sources += mono-hwcap-x86.c mono-hwcap-x86.h
endif

if AMD64
arch_sources += mono-hwcap-x86.c mono-hwcap-x86.h
endif

if ARM
arch_sources += mono-hwcap-arm.c mono-hwcap-arm.h
endif

if ARM64
arch_sources += mono-hwcap-arm64.c mono-hwcap-arm64.h
endif

if MIPS
arch_sources += mono-hwcap-mips.c mono-hwcap-mips.h
endif

if POWERPC
arch_sources += mono-hwcap-ppc.c mono-hwcap-ppc.h
endif

if POWERPC64
arch_sources += mono-hwcap-ppc.c mono-hwcap-ppc.h
endif

if SPARC
arch_sources += mono-hwcap-sparc.c mono-hwcap-sparc.h
endif

if SPARC64
arch_sources += mono-hwcap-sparc.c mono-hwcap-sparc.h
endif

if IA64
arch_sources += mono-hwcap-ia64.c mono-hwcap-ia64.h
endif

if S390X
arch_sources += mono-hwcap-s390x.c mono-hwcap-s390x.h
endif

libmonoutils_la_SOURCES = $(monoutils_sources) $(arch_sources)
libmonoutilsincludedir = $(includedir)/mono-$(API_VER)/mono/utils

libmonoutilsinclude_HEADERS = 	\
	mono-logger.h		\
	mono-error.h		\
	mono-publib.h		\
	mono-dl-fallback.h	\
	mono-counters.h

EXTRA_DIST = ChangeLog mono-embed.h mono-embed.c
