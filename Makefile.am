ACLOCAL_AMFLAGS = -I m4

SUBDIRS = $(CONFIG_SUBDIRS)

warningflags = -Wall -Wextra -Wno-unused-parameter -Wno-missing-field-initializers
commonflags = -O2 $(warningflags) $(DEBUGCFLAGS) $(PTHREAD_CFLAGS)
graphengineflags = -I$(srcdir)/graphengine/include -DGRAPHENGINE_IMPL_NAMESPACE=zimg
AM_CXXFLAGS = -std=$(CXXSTD) $(commonflags)
AM_CFLAGS = -std=c89 $(commonflags)
LDADD = $(PTHREAD_LIBS)


pkgconfigdir = $(libdir)/pkgconfig
pkgconfig_DATA = zimg.pc

EXTRA_DIST = zimg.pc.in


exampledir = $(docdir)/example
examplemiscdir = $(exampledir)/misc


dist_doc_DATA = ChangeLog COPYING README.md

dist_example_DATA = \
	doc/example/api_example.cpp \
	doc/example/api_example_c.c \
	doc/example/hdr_example.cpp \
	doc/example/interlace_example.cpp \
	doc/example/tile_example.cpp \
	doc/example/Makefile

dist_examplemisc_DATA = \
	src/testcommon/aligned_malloc.h \
	src/testcommon/argparse.cpp \
	src/testcommon/argparse.h \
	src/testcommon/mmap.cpp \
	src/testcommon/mmap.h \
	src/testcommon/win32_bitmap.cpp \
	src/testcommon/win32_bitmap.h


noinst_PROGRAMS =
lib_LTLIBRARIES = libzimg.la
noinst_LTLIBRARIES = libzimg_internal.la

include_HEADERS = \
	src/zimg/api/zimg.h \
	src/zimg/api/zimg++.hpp

libzimg_la_SOURCES = dummy.cpp
libzimg_la_LIBADD = libzimg_internal.la
libzimg_la_LDFLAGS = -no-undefined -version-info 2 -export-symbols-regex '^zimg_'

libzimg_internal_la_SOURCES = \
	graphengine/graphengine/cpuinfo.h \
	graphengine/graphengine/cpuinfo.cpp \
	graphengine/graphengine/graph.cpp \
	graphengine/graphengine/node.cpp \
	graphengine/graphengine/node.h \
	graphengine/graphengine/state.h \
	graphengine/graphengine/x86/cpuinfo_x86.cpp \
	graphengine/graphengine/x86/cpuinfo_x86.h \
	graphengine/include/graphengine/filter.h \
	graphengine/include/graphengine/graph.h \
	graphengine/include/graphengine/namespace.h \
	graphengine/include/graphengine/types.h \
	src/zimg/api/zimg.cpp \
	src/zimg/api/zimg.h \
	src/zimg/api/zimg++.hpp \
	src/zimg/colorspace/colorspace.cpp \
	src/zimg/colorspace/colorspace.h \
	src/zimg/colorspace/colorspace_graph.cpp \
	src/zimg/colorspace/colorspace_graph.h \
	src/zimg/colorspace/colorspace_param.cpp \
	src/zimg/colorspace/colorspace_param.h \
	src/zimg/colorspace/gamma.cpp \
	src/zimg/colorspace/gamma.h \
	src/zimg/colorspace/matrix3.cpp \
	src/zimg/colorspace/matrix3.h \
	src/zimg/colorspace/operation.cpp \
	src/zimg/colorspace/operation.h \
	src/zimg/colorspace/operation_impl.cpp \
	src/zimg/colorspace/operation_impl.h \
	src/zimg/common/align.h \
	src/zimg/common/alloc.h \
	src/zimg/common/builder.h \
	src/zimg/common/ccdep.h \
	src/zimg/common/checked_int.h \
	src/zimg/common/cpuinfo.cpp \
	src/zimg/common/cpuinfo.h \
	src/zimg/common/except.h \
	src/zimg/common/libm_wrapper.h \
	src/zimg/common/libm_wrapper.cpp \
	src/zimg/common/make_array.h \
	src/zimg/common/matrix.cpp \
	src/zimg/common/matrix.h \
	src/zimg/common/pixel.h \
	src/zimg/common/static_map.h \
	src/zimg/common/unroll.h \
	src/zimg/common/zassert.h \
	src/zimg/depth/blue.cpp \
	src/zimg/depth/blue.h \
	src/zimg/depth/depth_convert.cpp \
	src/zimg/depth/depth_convert.h \
	src/zimg/depth/depth.cpp \
	src/zimg/depth/depth.h \
	src/zimg/depth/dither.cpp \
	src/zimg/depth/dither.h \
	src/zimg/depth/quantize.h \
	src/zimg/depth/quantize.cpp \
	src/zimg/graph/filter_base.cpp \
	src/zimg/graph/filter_base.h \
	src/zimg/graph/filtergraph.cpp \
	src/zimg/graph/filtergraph.h \
	src/zimg/graph/graphbuilder.cpp \
	src/zimg/graph/graphbuilder.h \
	src/zimg/graph/graphengine_except.cpp \
	src/zimg/graph/graphengine_except.h \
	src/zimg/graph/simple_filters.cpp \
	src/zimg/graph/simple_filters.h \
	src/zimg/resize/filter.cpp \
	src/zimg/resize/filter.h \
	src/zimg/resize/resize.cpp \
	src/zimg/resize/resize.h \
	src/zimg/resize/resize_impl.cpp \
	src/zimg/resize/resize_impl.h \
	src/zimg/unresize/bilinear.cpp \
	src/zimg/unresize/bilinear.h \
	src/zimg/unresize/unresize.cpp \
	src/zimg/unresize/unresize.h \
	src/zimg/unresize/unresize_impl.cpp \
	src/zimg/unresize/unresize_impl.h

libzimg_internal_la_CPPFLAGS = $(AM_CPPFLAGS) -I$(srcdir)/src/zimg $(graphengineflags)
libzimg_internal_la_LIBADD =


if ARMSIMD
noinst_LTLIBRARIES += libneon.la

libzimg_internal_la_SOURCES += \
	src/zimg/colorspace/arm/operation_impl_arm.cpp \
	src/zimg/colorspace/arm/operation_impl_arm.h \
	src/zimg/common/arm/cpuinfo_arm.cpp \
	src/zimg/common/arm/cpuinfo_arm.h \
	src/zimg/common/arm/neon_util.cpp \
	src/zimg/common/arm/neon_util.h \
	src/zimg/depth/arm/depth_convert_arm.cpp \
	src/zimg/depth/arm/depth_convert_arm.h \
	src/zimg/depth/arm/dither_arm.cpp \
	src/zimg/depth/arm/dither_arm.h \
	src/zimg/resize/arm/resize_impl_arm.cpp \
	src/zimg/resize/arm/resize_impl_arm.h

libneon_la_SOURCES = \
	src/zimg/colorspace/arm/operation_impl_neon.cpp \
	src/zimg/depth/arm/depth_convert_neon.cpp \
	src/zimg/depth/arm/dither_neon.cpp \
	src/zimg/resize/arm/resize_impl_neon.cpp

libneon_la_CXXFLAGS = $(AM_CXXFLAGS) $(NEON_CFLAGS)
libneon_la_CPPFLAGS = $(AM_CPPFLAGS) -I$(srcdir)/src/zimg $(graphengineflags)

libzimg_internal_la_LIBADD += libneon.la
endif # ARMSIMD

if X86SIMD
noinst_LTLIBRARIES += libavx2.la libavx512.la libavx512_vnni.la

libzimg_internal_la_SOURCES += \
	src/zimg/colorspace/x86/operation_impl_x86.cpp \
	src/zimg/colorspace/x86/operation_impl_x86.h \
	src/zimg/common/x86/avx2_util.h \
	src/zimg/common/x86/avx512_util.h \
	src/zimg/common/x86/cpuinfo_x86.cpp \
	src/zimg/common/x86/cpuinfo_x86.h \
	src/zimg/common/x86/x86util.cpp \
	src/zimg/common/x86/x86util.h \
	src/zimg/depth/x86/depth_convert_x86.cpp \
	src/zimg/depth/x86/depth_convert_x86.h \
	src/zimg/depth/x86/dither_x86.cpp \
	src/zimg/depth/x86/dither_x86.h \
	src/zimg/resize/x86/resize_impl_x86.cpp \
	src/zimg/resize/x86/resize_impl_x86.h \
	src/zimg/unresize/x86/unresize_impl_x86.cpp \
	src/zimg/unresize/x86/unresize_impl_x86.h

libavx2_la_SOURCES = \
	src/zimg/colorspace/x86/operation_impl_avx2.cpp \
	src/zimg/depth/x86/depth_convert_avx2.cpp \
	src/zimg/depth/x86/dither_avx2.cpp \
	src/zimg/depth/x86/error_diffusion_avx2.cpp \
	src/zimg/resize/x86/resize_impl_avx2.cpp \
	src/zimg/unresize/x86/unresize_impl_avx2.cpp

libavx2_la_CXXFLAGS = $(AM_CXXFLAGS) -mavx2 -mf16c -mfma $(HSW_CFLAGS)
libavx2_la_CPPFLAGS = $(AM_CPPFLAGS) -I$(srcdir)/src/zimg $(graphengineflags)

libavx512_la_SOURCES = \
	src/zimg/colorspace/x86/gamma_constants_avx512.cpp \
	src/zimg/colorspace/x86/gamma_constants_avx512.h \
	src/zimg/colorspace/x86/operation_impl_avx512.cpp \
	src/zimg/depth/x86/depth_convert_avx512.cpp \
	src/zimg/depth/x86/dither_avx512.cpp \
	src/zimg/resize/x86/resize_impl_avx512.cpp \
	src/zimg/resize/x86/resize_impl_avx512_common.h

libavx512_la_CXXFLAGS = $(AM_CXXFLAGS) -mavx512f -mavx512cd -mavx512vl -mavx512bw -mavx512dq $(SKX_CFLAGS)
libavx512_la_CPPFLAGS = $(AM_CPPFLAGS) -I$(srcdir)/src/zimg $(graphengineflags)

libavx512_vnni_la_SOURCES = src/zimg/resize/x86/resize_impl_avx512_vnni.cpp
libavx512_vnni_la_CXXFLAGS = $(AM_CXXFLAGS) -mavx512f -mavx512cd -mavx512vl -mavx512bw -mavx512dq -mavx512vnni $(CLX_CFLAGS)
libavx512_vnni_la_CPPFLAGS = $(AM_CPPFLAGS) -I$(srcdir)/src/zimg $(graphengineflags)

libzimg_internal_la_LIBADD += libavx2.la libavx512.la libavx512_vnni.la
endif # X86SIMD


libtestcommon_la_SOURCES = \
	src/testcommon/aligned_malloc.h \
	src/testcommon/argparse.cpp \
	src/testcommon/argparse.h \
	src/testcommon/json.cpp \
	src/testcommon/json.h \
	src/testcommon/mmap.cpp \
	src/testcommon/mmap.h \
	src/testcommon/timer.h \
	src/testcommon/win32_bitmap.cpp \
	src/testcommon/win32_bitmap.h


if EXAMPLES
noinst_PROGRAMS += \
	doc/example/api_example \
	doc/example/api_example_c \
	doc/example/hdr_example \
	doc/example/interlace_example \
	doc/example/tile_example
noinst_LTLIBRARIES += libtestcommon.la

EXAMPLE_CPPFLAGS = $(AM_CPPFLAGS) -I$(srcdir)/src/zimg/api -I$(srcdir)/src/testcommon
EXAMPLE_LDADD = libtestcommon.la libzimg.la

doc_example_api_example_CPPFLAGS = $(EXAMPLE_CPPFLAGS)
doc_example_api_example_SOURCES = doc/example/api_example.cpp
doc_example_api_example_LDADD = $(EXAMPLE_LDADD)

doc_example_api_example_c_CPPFLAGS = $(EXAMPLE_CPPFLAGS)
doc_example_api_example_c_SOURCES = doc/example/api_example_c.c dummy.cpp
doc_example_api_example_c_LDADD = $(EXAMPLE_LDADD)

doc_example_hdr_example_CPPFLAGS = $(EXAMPLE_CPPFLAGS)
doc_example_hdr_example_SOURCES = doc/example/hdr_example.cpp
doc_example_hdr_example_LDADD = $(EXAMPLE_LDADD)

doc_example_interlace_example_CPPFLAGS = $(EXAMPLE_CPPFLAGS)
doc_example_interlace_example_SOURCES = doc/example/interlace_example.cpp
doc_example_interlace_example_LDADD = $(EXAMPLE_LDADD)

doc_example_tile_example_CPPFLAGS = $(EXAMPLE_CPPFLAGS)
doc_example_tile_example_SOURCES = doc/example/tile_example.cpp
doc_example_tile_example_LDADD = $(EXAMPLE_LDADD)
endif # EXAMPLES


if TESTAPP
noinst_PROGRAMS += testapp
noinst_LTLIBRARIES += libtestcommon.la
testapp_CPPFLAGS = $(AM_CPPFLAGS) -I$(srcdir)/src/zimg -I$(srcdir)/src/testcommon $(graphengineflags)

testapp_SOURCES = \
	src/testapp/apps.h \
	src/testapp/colorspaceapp.cpp \
	src/testapp/cpuinfoapp.cpp \
	src/testapp/depthapp.cpp \
	src/testapp/frame.cpp \
	src/testapp/frame.h \
	src/testapp/graphapp.cpp \
	src/testapp/main.cpp \
	src/testapp/resizeapp.cpp \
	src/testapp/table.cpp \
	src/testapp/table.h \
	src/testapp/unresizeapp.cpp \
	src/testapp/utils.cpp \
	src/testapp/utils.h

testapp_LDADD = libtestcommon.la libzimg_internal.la
endif # TESTAPP


if UNIT_TEST
TESTS = test/unit_test

check_LTLIBRARIES = test/libmusl_m.la
check_PROGRAMS = test/unit_test

test_libmusl_m_la_CFLAGS = $(AM_CFLAGS) -std=c99 -Wno-sign-compare -Wno-unused-variable -Wno-unused-but-set-variable

test_libmusl_m_la_SOURCES = \
	test/extra/musl-libm/__cos.c \
	test/extra/musl-libm/__math_divzerof.c \
	test/extra/musl-libm/__math_invalidf.c \
	test/extra/musl-libm/__math_oflowf.c \
	test/extra/musl-libm/__math_uflowf.c \
	test/extra/musl-libm/__math_xflowf.c \
	test/extra/musl-libm/__rem_pio2.c \
	test/extra/musl-libm/__rem_pio2_large.c \
	test/extra/musl-libm/__sin.c \
	test/extra/musl-libm/cos.c \
	test/extra/musl-libm/exp2f_data.c \
	test/extra/musl-libm/exp2f_data.h \
	test/extra/musl-libm/fpu_wrapper.c \
	test/extra/musl-libm/expf.c \
	test/extra/musl-libm/libm.h \
	test/extra/musl-libm/log10f.c \
	test/extra/musl-libm/logf.c \
	test/extra/musl-libm/logf_data.c \
	test/extra/musl-libm/logf_data.h \
	test/extra/musl-libm/mymath.h \
	test/extra/musl-libm/powf.c \
	test/extra/musl-libm/powf_data.c \
	test/extra/musl-libm/powf_data.h \
	test/extra/musl-libm/sin.c

test_unit_test_CPPFLAGS = \
	$(AM_CPPFLAGS) \
	-I$(srcdir)/src/zimg \
	-I$(srcdir)/test \
	-I$(srcdir)/test/extra \
	-I$(srcdir)/test/extra/googletest/googletest/include \
	$(graphengineflags)

test_unit_test_SOURCES = \
	graphengine/filter_validation/filter_validation.cpp \
	graphengine/filter_validation/sha1/config.h \
	graphengine/filter_validation/sha1/sha1.c \
	graphengine/filter_validation/sha1/sha1.h \
	graphengine/include/graphengine/filter_validation.h \
	test/dynamic_type.h \
	test/main.cpp \
	test/api/api_test.cpp \
	test/colorspace/colorspace_test.cpp \
	test/colorspace/gamma_test.cpp \
	test/depth/depth_convert_test.cpp \
	test/depth/dither_test.cpp \
	test/graph/graphbuilder_test.cpp \
	test/resize/filter_test.cpp \
	test/resize/resize_impl_test.cpp

if ARMSIMD
test_unit_test_SOURCES += \
	test/colorspace/arm/colorspace_neon_test.cpp \
	test/depth/arm/depth_convert_neon_test.cpp \
	test/depth/arm/dither_neon_test.cpp \
	test/resize/arm/resize_impl_neon_test.cpp
endif # ARMSIMD

if X86SIMD
test_unit_test_SOURCES += \
	test/colorspace/x86/colorspace_avx2_test.cpp \
	test/colorspace/x86/colorspace_avx512_test.cpp \
	test/colorspace/x86/gamma_constants_avx512_test.cpp \
	test/depth/x86/depth_convert_avx2_test.cpp \
	test/depth/x86/depth_convert_avx512_test.cpp \
	test/depth/x86/dither_avx2_test.cpp \
	test/depth/x86/dither_avx512_test.cpp \
	test/depth/x86/error_diffusion_avx2_test.cpp \
	test/resize/x86/resize_impl_avx2_test.cpp \
	test/resize/x86/resize_impl_avx512_test.cpp \
	test/resize/x86/resize_impl_avx512_vnni_test.cpp
endif # X86SIMD

test/extra/googletest/build/lib/libgtest.a: .FAKE
	-$(MAKE) -C test/extra/googletest/build gtest

.FAKE:

test_unit_test_LDADD = \
	test/extra/googletest/build/lib/libgtest.a \
	test/libmusl_m.la \
	libzimg_internal.la
endif # UNIT_TEST


clean-local:
	-cd test/extra/googletest/build && make clean

distclean-local:
	-rm -rf test/extra/googletest/build
