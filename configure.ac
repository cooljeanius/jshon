#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.69])
AC_INIT([jshon],[2014.01.26],[keenerd@gmail.com])
AC_CONFIG_SRCDIR([jshon.c])
AC_CONFIG_HEADERS([config.h])
AC_CONFIG_MACRO_DIR([m4])
AC_CONFIG_AUX_DIR([build-aux])
AC_CANONICAL_TARGET
AC_USE_SYSTEM_EXTENSIONS
AC_OBJEXT
AC_EXEEXT
AM_INIT_AUTOMAKE([gnits])
AM_MAINTAINER_MODE

# Checks for programs.
AC_DEFUN([AC_REQUIRE_COMPILER],[
  AC_REQUIRE([AC_PROG_CC])
  AC_REQUIRE([AC_PROG_CC_C_O])
  AC_REQUIRE([AM_PROG_CC_C_O])
  AC_REQUIRE([AC_PROG_CPP])
])
AC_REQUIRE_COMPILER
AC_PROG_INSTALL
AM_PROG_INSTALL_STRIP
AC_PROG_MKDIR_P
AC_PROG_SED
PKG_PROG_PKG_CONFIG

# Checks for libraries.
PKG_CHECK_MODULES([JANSSON],[jansson],[
test ! -z "${JANSSON_CFLAGS}" && export JANSSON_CFLAGS
test ! -z "${JANSSON_LIBS}" && export JANSSON_LIBS
CFLAGS="${CFLAGS} ${JANSSON_CFLAGS}"
CPPFLAGS="${CPPFLAGS} ${JANSSON_CFLAGS}"
LIBS="${LIBS} ${JANSSON_LIBS}"
])
AC_CHECK_LIB([jansson],[json_null])
AC_CHECK_LIB([c],[printf])

# Checks for header files.
AC_HEADER_STAT
AC_CHECK_HEADERS([ctype.h errno.h getopt.h jansson.h stdarg.h stdio.h \
                  sys/param.h windows.h])

# Checks for typedefs, structures, and compiler characteristics.
AC_SYS_LARGEFILE
AC_C_BIGENDIAN
AC_C_PROTOTYPES
AC_TYPE_SIZE_T
AC_TYPE_SSIZE_T
AC_CHECK_TYPES([ptrdiff_t])

# Checks for library functions.
AC_FUNC_MALLOC
AC_FUNC_REALLOC
AC_FUNC_STAT
AC_FUNC_STRTOD
AC_CHECK_FUNCS([asprintf exit fclose fopen fprintf fread free fwrite \
                isatty lseek puts qsort read start strcmp strdup \
                strerror strlen strncmp strtol])

AC_CONFIG_FILES([Makefile])
AC_OUTPUT
