# Compilation Flags
AM_CFLAGS = -g -O2 -I$(shell $(CC) -print-file-name=plugin)/include \
  -I$(top_srcdir)/include -fno-rtti
AM_LDFLAGS =
# Force us to be really specific with what we mean
AM_CFLAGS += -Wall -Wextra -Werror
AM_CXXFLAGS = $(CXXFLAGS) $(AM_CFLAGS)

# Build GCC Plugin
if ENABLE_GCC_PLUGIN
lib_LTLIBRARIES = libmageec_gcc.la
libmageec_gcc_la_SOURCES = feature-extract.cpp gcc-plugin.cpp \
  gcc-callbacks.cpp plugin-info.cpp
libmageec_gcc_la_LDFLAGS = -release 0.1.0
libmageec_gcc_la_LIBADD = ../mageec/libmageec.la

# GCC plugin specific headers for distribution
EXTRA_DIST = $(srcdir)/mageec-plugin.h

install-exec-hook:
	ln -sf $(DESTDIR)$(libdir)/libmageec_gcc.so `$(CC) -print-file-name=plugin`/mageec.so
uninstall-hook:
	rm -f `$(CC) -print-file-name=plugin`/mageec.so

endif

