include_directories(${CMAKE_SOURCE_DIR}/ccutil)

########### next target ###############

SET(tesseract_viewer_STAT_SRCS
   scrollview.cpp
   svmnode.cpp
   svutil.cpp
   svpaint.cpp
)

add_library(tesseract_viewer_static STATIC ${tesseract_viewer_STAT_SRCS})


########### next target ###############

SET(tesseract_viewer_LIB_SRCS ${DUMMY_CPP})

add_library(tesseract_viewer SHARED ${tesseract_viewer_LIB_SRCS})

target_link_libraries(tesseract_viewer)

set_target_properties(tesseract_viewer PROPERTIES VERSION 4.2.0 SOVERSION 4)
install(TARGETS tesseract_viewer DESTINATION lib)
install(TARGETS tesseract_viewer_static DESTINATION lib)


########### install files ###############




#original Makefile.am contents follow:

#AM_CPPFLAGS += -I$(top_srcdir)/ccutil
#
#if VISIBILITY
#AM_CPPFLAGS += -DTESS_EXPORTS \
#    -fvisibility=hidden -fvisibility-inlines-hidden
#endif
#
#noinst_HEADERS = \
#    scrollview.h svmnode.h svutil.h
#
#if !USING_MULTIPLELIBS
#noinst_LTLIBRARIES = libtesseract_viewer.la
#else
#lib_LTLIBRARIES = libtesseract_viewer.la
#libtesseract_viewer_la_LDFLAGS = -version-info $(GENERIC_LIBRARY_VERSION)
#endif
#
#libtesseract_viewer_la_SOURCES = \
#    scrollview.cpp svmnode.cpp svutil.cpp svpaint.cpp
