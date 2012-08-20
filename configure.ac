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
        [https://bugs.freedesktop.org/enter_bug.cgi?product=Mesa])
AC_CONFIG_SRCDIR([Makefile.am])
AC_CANONICAL_HOST

AM_INIT_AUTOMAKE([dist-bzip2 foreign subdir-objects])

dnl Check for progs
AC_PROG_CPP
AC_PROG_CC
AC_PROG_CXX
AC_PROG_LIBTOOL

dnl Enable quiet compiles on automake 1.11.
m4_ifdef([AM_SILENT_RULES], [AM_SILENT_RULES([yes])])

dnl Make sure the pkg-config macros are defined
m4_ifndef([PKG_PROG_PKG_CONFIG],
    [m4_fatal([Could not locate the pkg-config autoconf macros.
  These are usually located in /usr/share/aclocal/pkg.m4. If your macros
  are in a different location, try setting the environment variable
  ACLOCAL="aclocal -I/other/macro/dir" before running autoreconf.])])
PKG_PROG_PKG_CONFIG()

dnl Get the pkg-config definitions for libGL.  We include a fallback
dnl path for GL implementation that don't provide a .pc file
PKG_CHECK_MODULES(GL, [gl], [], [
          AC_CHECK_HEADER([GL/gl.h],
                  [],
                  AC_MSG_ERROR([GL not found]))
          AC_CHECK_LIB([GL],
                   [glBegin],
                   [GL_LIBS=-lGL],
                   AC_MSG_ERROR([GL required]))
          ])

dnl Set up C warning flags.
if test "x$GCC" = xyes; then
    CFLAGS="$CFLAGS -Wall"
    CXXFLAGS="$CXXFLAGS -Wall"
else
    AC_CHECK_DECL([__SUNPRO_C], [SUNCC="yes"], [SUNCC="no"])
    if test "x$SUNCC" = "xyes"; then
        WARNFLAGS="-v"
    fi
fi

AC_OUTPUT([
    Makefile
    glu.pc
])
