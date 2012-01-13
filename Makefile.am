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

pkgconfigdir = $(libdir)/pkgconfig
pkgconfig_DATA = glu.pc

ACLOCAL_AMFLAGS = ${ACLOCAL_FLAGS}

AM_CPPFLAGS = -DLIBRARYBUILD \
	-I$(top_srcdir)/include \
	-I$(top_srcdir)/src/include \
	-I$(top_srcdir)/src/libnurbs/internals \
	-I$(top_srcdir)/src/libnurbs/interface \
	-I$(top_srcdir)/src/libnurbs/nurbtess

GLU_LIBRARY_VERSION=1:3:1
lib_LTLIBRARIES = libGLU.la
libGLU_la_SOURCES =						\
	src/libutil/error.c					\
	src/libutil/glue.c					\
	src/libutil/mipmap.c					\
	src/libutil/project.c					\
	src/libutil/quad.c					\
	src/libutil/registry.c					\
	src/libtess/dict.c					\
	src/libtess/geom.c					\
	src/libtess/memalloc.c					\
	src/libtess/mesh.c					\
	src/libtess/normal.c					\
	src/libtess/priorityq.c					\
	src/libtess/render.c					\
	src/libtess/sweep.c					\
	src/libtess/tess.c					\
	src/libtess/tessmono.c					\
	src/libnurbs/interface/bezierEval.cc			\
	src/libnurbs/interface/bezierPatch.cc			\
	src/libnurbs/interface/bezierPatchMesh.cc		\
	src/libnurbs/interface/glcurveval.cc			\
	src/libnurbs/interface/glinterface.cc			\
	src/libnurbs/interface/glrenderer.cc			\
	src/libnurbs/interface/glsurfeval.cc			\
	src/libnurbs/interface/incurveeval.cc			\
	src/libnurbs/interface/insurfeval.cc			\
	src/libnurbs/internals/arc.cc				\
	src/libnurbs/internals/arcsorter.cc			\
	src/libnurbs/internals/arctess.cc			\
	src/libnurbs/internals/backend.cc			\
	src/libnurbs/internals/basiccrveval.cc			\
	src/libnurbs/internals/basicsurfeval.cc			\
	src/libnurbs/internals/bin.cc				\
	src/libnurbs/internals/bufpool.cc			\
	src/libnurbs/internals/cachingeval.cc			\
	src/libnurbs/internals/ccw.cc				\
	src/libnurbs/internals/coveandtiler.cc			\
	src/libnurbs/internals/curve.cc				\
	src/libnurbs/internals/curvelist.cc			\
	src/libnurbs/internals/curvesub.cc			\
	src/libnurbs/internals/dataTransform.cc			\
	src/libnurbs/internals/displaylist.cc			\
	src/libnurbs/internals/flist.cc				\
	src/libnurbs/internals/flistsorter.cc			\
	src/libnurbs/internals/hull.cc				\
	src/libnurbs/internals/intersect.cc			\
	src/libnurbs/internals/knotvector.cc			\
	src/libnurbs/internals/mapdesc.cc			\
	src/libnurbs/internals/mapdescv.cc			\
	src/libnurbs/internals/maplist.cc			\
	src/libnurbs/internals/mesher.cc			\
	src/libnurbs/internals/monoTriangulationBackend.cc	\
	src/libnurbs/internals/monotonizer.cc			\
	src/libnurbs/internals/mycode.cc			\
	src/libnurbs/internals/nurbsinterfac.cc			\
	src/libnurbs/internals/nurbstess.cc			\
	src/libnurbs/internals/patch.cc				\
	src/libnurbs/internals/patchlist.cc			\
	src/libnurbs/internals/quilt.cc				\
	src/libnurbs/internals/reader.cc			\
	src/libnurbs/internals/renderhints.cc			\
	src/libnurbs/internals/slicer.cc			\
	src/libnurbs/internals/sorter.cc			\
	src/libnurbs/internals/splitarcs.cc			\
	src/libnurbs/internals/subdivider.cc			\
	src/libnurbs/internals/tobezier.cc			\
	src/libnurbs/internals/trimline.cc			\
	src/libnurbs/internals/trimregion.cc			\
	src/libnurbs/internals/trimvertpool.cc			\
	src/libnurbs/internals/uarray.cc			\
	src/libnurbs/internals/varray.cc			\
	src/libnurbs/nurbtess/directedLine.cc			\
	src/libnurbs/nurbtess/gridWrap.cc			\
	src/libnurbs/nurbtess/monoChain.cc			\
	src/libnurbs/nurbtess/monoPolyPart.cc			\
	src/libnurbs/nurbtess/monoTriangulation.cc		\
	src/libnurbs/nurbtess/partitionX.cc			\
	src/libnurbs/nurbtess/partitionY.cc			\
	src/libnurbs/nurbtess/polyDBG.cc			\
	src/libnurbs/nurbtess/polyUtil.cc			\
	src/libnurbs/nurbtess/primitiveStream.cc		\
	src/libnurbs/nurbtess/quicksort.cc			\
	src/libnurbs/nurbtess/rectBlock.cc			\
	src/libnurbs/nurbtess/sampleComp.cc			\
	src/libnurbs/nurbtess/sampleCompBot.cc			\
	src/libnurbs/nurbtess/sampleCompRight.cc		\
	src/libnurbs/nurbtess/sampleCompTop.cc			\
	src/libnurbs/nurbtess/sampleMonoPoly.cc			\
	src/libnurbs/nurbtess/sampledLine.cc			\
	src/libnurbs/nurbtess/searchTree.cc
libGLU_la_CFLAGS = $(GL_CFLAGS)
libGLU_la_LIBADD = $(GL_LIBS)
libGLU_la_LDFLAGS = -version-number $(GLU_LIBRARY_VERSION) -no-undefined -export-symbols-regex '^glu'
