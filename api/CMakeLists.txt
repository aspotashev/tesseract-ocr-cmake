include_directories(${CMAKE_SOURCE_DIR}/ccutil)
include_directories(${CMAKE_SOURCE_DIR}/ccstruct)
include_directories(${CMAKE_SOURCE_DIR}/cube)
include_directories(${CMAKE_SOURCE_DIR}/viewer)
include_directories(${CMAKE_SOURCE_DIR}/textord)
include_directories(${CMAKE_SOURCE_DIR}/dict)
include_directories(${CMAKE_SOURCE_DIR}/classify)
include_directories(${CMAKE_SOURCE_DIR}/ccmain)
include_directories(${CMAKE_SOURCE_DIR}/wordrec)
include_directories(${CMAKE_SOURCE_DIR}/cutil)
include_directories(${CMAKE_SOURCE_DIR}/opencl)
include_directories(${CMAKE_SOURCE_DIR}/msvsport)

########### next target ###############

SET(tesseract_api_STAT_SRCS
   baseapi.cpp
   capi.cpp
   pdfrenderer.cpp
   renderer.cpp
)

# AM_CPPFLAGS += -DLOCALEDIR=\"$(localedir)\"\
#     -DUSE_STD_NAMESPACE \
#     -I$(top_srcdir)/ccutil -I$(top_srcdir)/ccstruct -I$(top_srcdir)/cube \
#     -I$(top_srcdir)/viewer \
#     -I$(top_srcdir)/textord -I$(top_srcdir)/dict \
#     -I$(top_srcdir)/classify -I$(top_srcdir)/ccmain \
#     -I$(top_srcdir)/wordrec -I$(top_srcdir)/cutil \
#     -I$(top_srcdir)/opencl

add_library(tesseract_api_static STATIC ${tesseract_api_STAT_SRCS})
target_link_libraries(tesseract_api_static
    tesseract_main
#     ../cube/libtesseract_cube.la \
#     ../neural_networks/runtime/libtesseract_neural.la \
#     ../textord/libtesseract_textord.la \
#     ../wordrec/libtesseract_wordrec.la \
#     ../classify/libtesseract_classify.la \
#     ../dict/libtesseract_dict.la \
#     ../ccstruct/libtesseract_ccstruct.la \
#     ../cutil/libtesseract_cutil.la \
#     ../viewer/libtesseract_viewer.la \
#     ../ccutil/libtesseract_ccutil.la \
#     ../opencl/libtesseract_opencl.la
  )

install(TARGETS tesseract_api_static DESTINATION lib)

########### next target ###############

# SET(tesseract_SRCS
#    tesseractmain.cpp
# )
#
# add_executable(tesseract ${tesseract_SRCS})
#
# target_link_libraries(tesseract tesseract)
#
# install(TARGETS tesseract DESTINATION bin)


########### install files ###############

install(
    FILES
        apitypes.h baseapi.h capi.h renderer.h
    DESTINATION
        include/tesseract
)


#original Makefile.am contents follow:

#AM_CPPFLAGS += -DLOCALEDIR=\"$(localedir)\"\
#    -DUSE_STD_NAMESPACE \
#    -I$(top_srcdir)/ccutil -I$(top_srcdir)/ccstruct -I$(top_srcdir)/cube \
#    -I$(top_srcdir)/viewer \
#    -I$(top_srcdir)/textord -I$(top_srcdir)/dict \
#    -I$(top_srcdir)/classify -I$(top_srcdir)/ccmain \
#    -I$(top_srcdir)/wordrec -I$(top_srcdir)/cutil \
#    -I$(top_srcdir)/opencl
#if USE_OPENCL
#AM_CPPFLAGS += -I$(OPENCL_HDR_PATH)
#endif
#if VISIBILITY
#AM_CPPFLAGS += -fvisibility=hidden -fvisibility-inlines-hidden
#endif
#
#include_HEADERS = apitypes.h baseapi.h capi.h renderer.h
#lib_LTLIBRARIES = 
#
#if !USING_MULTIPLELIBS
#noinst_LTLIBRARIES = libtesseract_api.la
#else
#lib_LTLIBRARIES += libtesseract_api.la
#libtesseract_api_la_LDFLAGS = -version-info $(GENERIC_LIBRARY_VERSION)
#libtesseract_api_la_LIBADD = \
#    ../ccmain/libtesseract_main.la \
#    ../cube/libtesseract_cube.la \
#    ../neural_networks/runtime/libtesseract_neural.la \
#    ../textord/libtesseract_textord.la \
#    ../wordrec/libtesseract_wordrec.la \
#    ../classify/libtesseract_classify.la \
#    ../dict/libtesseract_dict.la \
#    ../ccstruct/libtesseract_ccstruct.la \
#    ../cutil/libtesseract_cutil.la \
#    ../viewer/libtesseract_viewer.la \
#    ../ccutil/libtesseract_ccutil.la \
#    ../opencl/libtesseract_opencl.la 
#
#endif
#libtesseract_api_la_CPPFLAGS = $(AM_CPPFLAGS)
#if VISIBILITY
#libtesseract_api_la_CPPFLAGS += -DTESS_EXPORTS
#endif
#libtesseract_api_la_SOURCES = baseapi.cpp capi.cpp pdfrenderer.cpp renderer.cpp
#
#lib_LTLIBRARIES += libtesseract.la
#libtesseract_la_LDFLAGS = 
#libtesseract_la_SOURCES = dummy.cxx
## Dummy C++ source to cause C++ linking.
## see http://www.gnu.org/s/hello/manual/automake/Libtool-Convenience-Libraries.html#Libtool-Convenience-Libraries
## nodist_EXTRA_libtesseract_la_SOURCES = dummy.cxx
#libtesseract_la_LIBADD = \
#    libtesseract_api.la \
#    ../ccmain/libtesseract_main.la \
#    ../cube/libtesseract_cube.la \
#    ../neural_networks/runtime/libtesseract_neural.la \
#    ../textord/libtesseract_textord.la \
#    ../wordrec/libtesseract_wordrec.la \
#    ../classify/libtesseract_classify.la \
#    ../dict/libtesseract_dict.la \
#    ../ccstruct/libtesseract_ccstruct.la \
#    ../cutil/libtesseract_cutil.la \
#    ../viewer/libtesseract_viewer.la \
#    ../ccutil/libtesseract_ccutil.la \
#    ../opencl/libtesseract_opencl.la 
#
#libtesseract_la_LDFLAGS += -version-info $(GENERIC_LIBRARY_VERSION)
#
#bin_PROGRAMS = tesseract
#tesseract_SOURCES = tesseractmain.cpp
#tesseract_CPPFLAGS = $(AM_CPPFLAGS)
#if VISIBILITY
#tesseract_CPPFLAGS += -DTESS_IMPORTS
#endif
#
#tesseract_LDADD = libtesseract.la
#
#if USE_OPENCL
#tesseract_LDADD += $(OPENCL_LIB)
#endif
#
#if T_WIN
#tesseract_LDADD += -lws2_32
#libtesseract_la_LDFLAGS += -no-undefined -Wl,--as-needed -lws2_32
#endif
#if ADD_RT
#tesseract_LDADD += -lrt
#endif
#
