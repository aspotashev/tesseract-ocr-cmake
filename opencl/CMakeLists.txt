include_directories(${CMAKE_SOURCE_DIR}/ccutil)
include_directories(${CMAKE_SOURCE_DIR}/ccstruct)
include_directories(${CMAKE_SOURCE_DIR}/ccmain)

########### next target ###############

SET(tesseract_opencl_STAT_SRCS
   openclwrapper.cpp
)

add_library(tesseract_opencl_static STATIC ${tesseract_opencl_STAT_SRCS})


########### next target ###############

SET(tesseract_opencl_LIB_SRCS ${DUMMY_CPP})

add_library(tesseract_opencl SHARED ${tesseract_opencl_LIB_SRCS})

target_link_libraries(tesseract_opencl)

set_target_properties(tesseract_opencl PROPERTIES VERSION 4.2.0 SOVERSION 4)
install(TARGETS tesseract_opencl DESTINATION lib)
install(TARGETS tesseract_opencl_static DESTINATION lib)


########### install files ###############




#original Makefile.am contents follow:

#AM_CPPFLAGS += -I$(top_srcdir)/ccutil -I$(top_srcdir)/ccstruct -I$(top_srcdir)/ccmain 
#if USE_OPENCL
#AM_CPPFLAGS += -I$(OPENCL_HDR_PATH)
#endif
#noinst_HEADERS = \
#    openclwrapper.h oclkernels.h opencl_device_selection.h 
#
#if !USING_MULTIPLELIBS
#noinst_LTLIBRARIES = libtesseract_opencl.la
#else
#lib_LTLIBRARIES = libtesseract_opencl.la
#libtesseract_opencl_la_LDFLAGS = -version-info $(GENERIC_LIBRARY_VERSION)
#libtesseract_opencl_la_LIBADD = \
#    ../ccutil/libtesseract_ccutil.la \
#    ../viewer/libtesseract_viewer.la
#if USE_OPENCL
#libtesseract_opencl_la_LDFLAGS += $(OPENCL_LIB)
#endif
#endif
#
#libtesseract_opencl_la_SOURCES = \
#    openclwrapper.cpp
