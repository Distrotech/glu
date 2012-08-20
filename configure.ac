# Copyright © 2011 Intel Corporation
#
# Permission is hereby granted, free of charge, to any person obtaining a
# copy of this software and associated documentation files (the "Software"),
# to deal in the Software without restriction, including without limitation
# the rights to use, copy, modify, merge, publish, distribute, sublicense,
# and/or sell copies of the Software, and to permit persons to whom the
# Software is furnished to do so, subject to the following conditions:
#
# The above copyright notice and this permission notice (including the next
# paragraph) shall be included in all copies or substantial portions of the
# Software.
#
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.  IN NO EVENT SHALL
# THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
# LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
# FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS
# IN THE SOFTWARE.

AC_PREREQ([2.60])
AC_INIT([glu],
        [1.3.1],
        [https://bugs.freedesktop.org/enter_bug.cgi?product=Mesa&component=GLU])
AC_CONFIG_SRCDIR([Makefile.am])
AC_CANONICAL_HOST

AM_INIT_AUTOMAKE([dist-bzip2 foreign subdir-objects])

LT_PREREQ([2.2])
LT_INIT

dnl Check for progs
AC_PROG_CPP
AC_PROG_CC
AC_PROG_CXX

dnl Enable quiet compiles on automake 1.11.
m4_ifdef([AM_SILENT_RULES], [AM_SILENT_RULES([yes])])

dnl Make sure the pkg-config macros are defined
m4_ifndef([PKG_PROG_PKG_CONFIG],
    [m4_fatal([Could not locate the pkg-config autoconf macros.
  These are usually located in /usr/share/aclocal/pkg.m4. If your macros
  are in a different location, try setting the environment variable
  ACLOCAL="aclocal -I/other/macro/dir" before running autoreconf.])])
PKG_PROG_PKG_CONFIG()

AC_ARG_ENABLE(osmesa,
              AS_HELP_STRING([--enable-osmesa],
                [Enable use of OSMesa instead of libGL]),
              [OSMESA="$enableval"],
              [OSMESA=no])

dnl Get the pkg-config definitions for libGL/OSMesa.  We include a fallback
dnl path for implementations that don't provide a .pc file
if test "x$OSMESA" = "xyes"; then
    PKG_CHECK_MODULES(OSMESA, [osmesa], [], [
          AC_CHECK_HEADER([GL/osmesa.h],
                  [],
                  AC_MSG_ERROR([OSMesa not found]))
          AC_CHECK_LIB([OSMesa],
                   [glBegin],
                   [OSMESA_LIBS=-lOSMesa],
                   AC_MSG_ERROR([OSMesa required]))
          ])
else
    PKG_CHECK_MODULES(GL, [gl], [], [
          AC_CHECK_HEADER([GL/gl.h],
                  [],
                  AC_MSG_ERROR([GL not found]))
          AC_CHECK_LIB([GL],
                   [glBegin],
                   [GL_LIBS=-lGL],
                   AC_MSG_ERROR([GL required]))
          ])
fi

dnl Set up C warning flags.
if test "x$GCC" = xyes; then
    WARNCFLAGS="-Wall"
    if test "x$GXX" = xyes; then
        WARNCXXFLAGS="-Wall"
    fi
else
    AC_CHECK_DECL([__SUNPRO_C], [SUNCC="yes"], [SUNCC="no"])
    if test "x$SUNCC" = "xyes"; then
        WARNCFLAGS="-v"
        WARNCXXFLAGS="-v"
    fi
fi
AC_SUBST([WARNCFLAGS])
AC_SUBST([WARNCXXFLAGS])

AC_OUTPUT([
    Makefile
    glu.pc
])
