include_directories(${CMAKE_SOURCE_DIR}/ccutil)
include_directories(${CMAKE_SOURCE_DIR}/viewer)

########### next target ###############

SET(tesseract_cutil_STAT_SRCS
   bitvec.cpp
   callcpp.cpp
   cutil.cpp
   cutil_class.cpp
   danerror.cpp
   efio.cpp
   emalloc.cpp
   freelist.cpp
   listio.cpp
   oldlist.cpp
   structures.cpp
)

add_library(tesseract_cutil_static STATIC ${tesseract_cutil_STAT_SRCS})


########### next target ###############

SET(tesseract_cutil_LIB_SRCS ${DUMMY_CPP})

add_library(tesseract_cutil SHARED ${tesseract_cutil_LIB_SRCS})

target_link_libraries(tesseract_cutil)

set_target_properties(tesseract_cutil PROPERTIES VERSION 4.2.0 SOVERSION 4)
install(TARGETS tesseract_cutil DESTINATION lib)
install(TARGETS tesseract_cutil_static DESTINATION lib)


########### install files ###############




#original Makefile.am contents follow:

#AM_CPPFLAGS += -I$(top_srcdir)/ccutil -I$(top_srcdir)/viewer
#
#if VISIBILITY
#AM_CPPFLAGS += -DTESS_EXPORTS \
#    -fvisibility=hidden -fvisibility-inlines-hidden
#endif
#
#noinst_HEADERS = \
#    bitvec.h callcpp.h const.h cutil.h cutil_class.h danerror.h efio.h \
#    emalloc.h freelist.h globals.h listio.h \
#    oldlist.h structures.h
#
#if !USING_MULTIPLELIBS
#noinst_LTLIBRARIES = libtesseract_cutil.la
#else
#lib_LTLIBRARIES = libtesseract_cutil.la
#libtesseract_cutil_la_LDFLAGS = -version-info $(GENERIC_LIBRARY_VERSION)
#libtesseract_cutil_la_LIBADD = \
#	../ccutil/libtesseract_ccutil.la \
#	../viewer/libtesseract_viewer.la	
#endif
#
#libtesseract_cutil_la_SOURCES = \
#    bitvec.cpp callcpp.cpp cutil.cpp cutil_class.cpp danerror.cpp efio.cpp \
#    emalloc.cpp freelist.cpp listio.cpp \
#    oldlist.cpp structures.cpp
#
#
